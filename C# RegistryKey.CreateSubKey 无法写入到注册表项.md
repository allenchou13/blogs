# C# RegistryKey.CreateSubKey 无法写入到注册表项

```cs
        var extensionsKey = pfuKey.OpenSubKey(@"PARENT KEY NAME");
        var extKey = extensionsKey.CreateSubKey("SUBKEY NAME");
```

异常: System.UnauthorizedAccessException: 无法写入到注册表项

## 解决方法

OpenSubKey 第二个参数设为true

```cs
        var extensionsKey = pfuKey.OpenSubKey(@"PARENT KEY NAME", true);
        var extKey = extensionsKey.CreateSubKey("SUBKEY NAME");
```