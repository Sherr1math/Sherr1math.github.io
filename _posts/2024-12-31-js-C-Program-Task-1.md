---
layout: post
title: "2024 Fall C-Programming Homework"
subtitle: "2 Tasks"
author: "Sherr1"
# header-style: text
header-img: "img/bg10.png"
catalog: true
mathjax: true
tags:
  - C
  - Code
---

## Introduction
本学期我也选了C程序语言设计，这门课一共有五次提交作业，其中前三次的作业过于简单，最后两次作业还是有点意思的.

### Homework 4
> 1.了解csv格式文件。
>2.通过excel软件，创建两个表格，内容是M\*N, N\*Q 浮点数矩阵，数值随意。保存为a.xlsx,b.xlsx文件。其中 M，N，Q是自然数，均不小于4。
>3. 将上述excel文件另存为 a.csv,b.csv文件.
>4.编写程序，通过命令行方式，读取这两个csv数据文件，并实现矩阵乘法，将原矩阵数据和矩阵乘法结果数据输出到屏幕。
>5.程序中矩阵维数，不得是定值，需通过读取csv文件获得。
>6. 源程序打包zip，运行结果截图。

我的C语言程序(用 Dev C++ 写的)：
```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

double** readcsv(const char* filename, int* rows, int* cols)
{
    FILE* file = fopen(filename, "r");
    if (file == NULL)
	{
        perror("Error opening file");
        return NULL;
    }

    char line[1024];
    int row = 0;
    int col = 0;

    while (fgets(line, sizeof(line), file))
	{
        row++;
        col = 0;
        char* token = strtok(line, ",");
        while (token!= NULL)
		{
            col++;
            token = strtok(NULL, ",");
        }
    }

    fseek(file, 0, SEEK_SET);

    double** matrix = (double**)malloc(row * sizeof(double*));
    for (int i = 0; i < row; i++)
	{
        matrix[i] = (double*)malloc(col * sizeof(double));
    }

    row = 0;
    while (fgets(line, sizeof(line), file))
	{
        col = 0;
        char* token = strtok(line, ",");
        while (token!= NULL)
		{
            matrix[row][col] = atof(token);
            col++;
            token = strtok(NULL, ",");
        }
        row++;
    }

    fclose(file);

    *rows = row;
    *cols = col;
    return matrix;
}

double** plusMat(double** matrix1, int rows1, int cols1, double** matrix2, int rows2, int cols2) {
    if (cols1!= rows2)
	{
        printf("Error: Incompatible matrix dimensions for multiplication.\n");
        return NULL;
    }

    double** result = (double**)malloc(rows1 * sizeof(double*));
    for (int i = 0; i < rows1; i++)
	{
        result[i] = (double*)malloc(cols2 * sizeof(double));
        for (int j = 0; j < cols2; j++)
		{
            result[i][j] = 0;
            for (int k = 0; k < cols1; k++)
			{
                result[i][j] += matrix1[i][k] * matrix2[k][j];
            }
        }
    }

    return result;
}

void freeMat(double** matrix, int rows)
{
    for (int i = 0; i < rows; i++)
	{
        free(matrix[i]);
    }
    free(matrix);
}

void printMat(double** matrix, int rows, int cols)
{
    for (int i = 0; i < rows; i++)
	{
        for (int j = 0; j < cols; j++)
		{
            printf("%.10f ", matrix[i][j]);
        }
        printf("\n");
    }
}

int main(int argc, char* argv[])
{
    int rows1, cols1;
    //char *filename1="A.csv";
    double** matrix1 = readcsv("a.csv", &rows1, &cols1);
    if (matrix1 == NULL)
	{
        return 1;
    }

    int rows2, cols2;
    //char *filename2="B.csv";
    double** matrix2 = readcsv("b.csv", &rows2, &cols2);
    if (matrix2 == NULL)
	{
        freeMat(matrix1, rows1);
        return 1;
    }

    double** result = plusMat(matrix1, rows1, cols1, matrix2, rows2, cols2);
    if (result == NULL)
	{
        freeMat(matrix1, rows1);
        freeMat(matrix2, rows2);
        return 1;
    }

    printf("Matrix A:\n");
    printMat(matrix1, rows1, cols1);

    printf("\nMatrix B:\n");
    printMat(matrix2, rows2, cols2);

    printf("\nA * B:\n");
    printMat(result, rows1, cols2);

    freeMat(matrix1, rows1);
    freeMat(matrix2, rows2);
    freeMat(result, rows1);

    return 0;
}
```

### Homework 5
>1. 了解json文件格式
>2. 使用C编写程序解析test.json
>3. 打印输出json内容（按照字段输出）
>4. 可使用各类开源库cJSON，Morn，Melon等，不限制

任务中的 [test.json](/files/Code/C/Example/test.json)

我采用的是 **cJSON** 库来读取 **json** 文件。

其中 **cJSON** 库的下载来自 **Github** 中的资源，在进行编写我们的程序之前(我是用 VisualStudio 来编写的)，需要将下载的 **cJSON** 库中的 **cJSON.c** 和 **cJSON.h** 添加到我们建立的项目中的源代码里，同时在编写程序过程中我也遇到了 **cJSON** 库无法调用的情形，这需要更改该项目的“包含目录”(在 Visual Studio 中更改)。

首先用 **fopen** 函数打开文件 **test.json** ，读取文件内容到一个字符串 **file** 中，然后使用 **cJSON_Parse** 函数解析这个字符串得到一个 **cJSON** 对象。接着，程序调用 **print_json** 函数来打印这个 **cJSON** 对象的内容。 **print_json** 函数递归地遍历cJSON对象的所有子节点，并打印它们的类型和值。最后，程序释放 **cJSON** 对象所占用的内存并退出。

值得注意的是，如果只是按照上述程序读入最终输出的 **json** 文件中的内容中的英文和数字均输出正常，但是 **json** 文件中的中文内容输出结果为乱码。我一直不知道原因在哪，最终的解决做法是将 json 文件中的文件编码在 Visual Studio 中改成 **UTF-8(带签名)** 这样的格式才行，感觉可能是由于编码格式不同所导致的最终中文显示的错乱。

我的C语言程序(用 Visual Studio 写的)：
```C
#include <iostream>

extern "C" {
#include <string.h>
#include <stdio.h>
#include "cJSON.h"
}

void print_json(cJSON* json) {
    if (json == NULL) return;

    if (json->type == cJSON_Object) {
        cJSON* child = json->child;
        while (child) {
            printf("%s: ", child->string);
            print_json(child);
            child = child->next;
        }
    }
    else if (json->type == cJSON_Array) {
        int i;
        for (i = 0; i < cJSON_GetArraySize(json); i++) {
            printf("[%d]: ", i);
            print_json(cJSON_GetArrayItem(json, i));
        }
    }
    else if (json->type == cJSON_String) {
        printf("%s", json->valuestring);
    }
    else if (json->type == cJSON_Number) {
        printf("%d", json->valueint);
    }
    else {
        printf("Unknown type");
    }
    printf("\n");
}

int main() {
    FILE* file = fopen("test.json", "r");
    if (file == NULL) {
        printf("Failed to open file\n");
        return 1;
    }

    fseek(file, 0, SEEK_END);
    long file_size = ftell(file);
    fseek(file, 0, SEEK_SET);

    char* json_str = (char*)malloc(file_size + 1);
    fread(json_str, 1, file_size, file);
    fclose(file);

    json_str[file_size] = '\0';

    cJSON* json = cJSON_Parse(json_str);
    free(json_str);

    if (json == NULL) {
        printf("Failed to parse JSON\n");
        return 1;
    }

    print_json(json);

    cJSON_Delete(json);
    return 0;
}
```
## Remark
If you have any questions or need further assistance, feel free to ask! Here is my email: [nkusherr1 at gmail.com](mailto:nkusherr1@gmail.com)
