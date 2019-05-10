# python json raise JSONDecodeError: Invalid \escape

python中json模块会解释转义字符,如`\n`等，如果出现不合法的转义字符，如`\U`，则会报错，解决方法如下：

```python

dest = json.loads(src.replace("\\", "\\\\"))

```
