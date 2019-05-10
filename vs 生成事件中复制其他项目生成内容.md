# vs 生成事件中复制其他项目生成内容

```cmd
xcopy /S /E /Y <src_dir>\*.* <dest_dir>
```

- /Y 取消确认是否覆盖的提示
- /S 复制子目录
- /E 复制空目录
- <src_dir> 源目录
- <dest_dir> 目标目录

注意： `xcopy <src_dir> <dest_dir>` 是复制src_dir下所有文件到dest_dir下