# Excel换行问题

问题代码：

```cs
ExcelWorksheet ws;
ws.Cells[i,j].Value = "First Line\nSecond Line\r\nThird Line";
```

结果生成的Excel文件使用Excel软件打开后不会换行显示，即换行符在excel中无效，Ctl+C复制Excel单元格，粘贴到文本编辑器中，换行符还在。

使用的是EPPlus

解决方法：

```cs
ws.Cells[i,j].Style.WrapText = true;
```

## 参考

- [Insert new line into excel EPPlus](https://stackoverflow.com/questions/38372992/insert-new-line-into-excel-epplus)