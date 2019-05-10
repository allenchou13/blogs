# C# ini file 操作

```cs
using System;
using System.Runtime.InteropServices;
using System.Text;

namespace Ini
{
    public class Sample
    {
        [DllImport("kernel32")]
        private static extern long WritePrivateProfileString(string section, string key,string val,string filePath);

        [DllImport("kernel32")]
        private static extern int GetPrivateProfileString(string section, string key,string def, StringBuilder retVal, int size,string filePath);

        public void IniWriteValue()
        {
            string path = "";
            string Section = "Common";  // [Common] section
            string Key = "path";
            string Value = "value";
            WritePrivateProfileString(Section, Key, Value, path);
        }


        public string IniReadValue()
        {
            string path = "";
            string Section = "";
            string Key = "";
            StringBuilder temp = new StringBuilder(255);
            int i = GetPrivateProfileString(Section, Key, "", temp, 255, path);
            return temp.ToString();
        }

    }
}
```
