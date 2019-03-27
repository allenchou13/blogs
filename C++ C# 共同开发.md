# C++ C# 共同开发

有时候需要用到C++、C#语言共同开发的技术，C++编译的动态库有运行效率高，逆向工程难度大的好处。

## C++代码示例

```
    extern "C" __declspec(dllexport) char* get_a() {
        char *a = new char[5];
        strcpy_s(a, 5, "1234");
        return a;
    }
```

## C#代码示例

```
        [DllImport("Dll1.dll", EntryPoint = "get_a")]
        private static extern IntPtr get_a_native();

        public static string get_a()
        {
            var charptr = get_a_native();
            var str = Marshal.PtrToStringAnsi(charptr);
            return str;
        }
```

## UTF8字符编码的C#获取字符串方法

```
        private unsafe static string PtrToString(IntPtr ptr)
        {
            byte* byteptr = (byte*)ptr.ToPointer();
            int size = 0;
            while (byteptr[size] != 0)
            {
                size++;
            }
            byte[] buffer = new byte[size];
            Marshal.Copy(ptr, buffer, 0, size);
            return Encoding.UTF8.GetString(buffer);
        }
```
