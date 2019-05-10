# linq 如何分组并排序

```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

namespace ConsoleApp1
{
    class Item
    {
        public string BatchName { get; set; }
        public int Number { get; set; }

        public override string ToString()
        {
            return $"{BatchName}--{Number}";
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            var list = new List<Item>();
            list.Add(new Item { BatchName = "BOne", Number = 10 });
            list.Add(new Item { BatchName = "BTwo", Number = 3 });
            list.Add(new Item { BatchName = "BOne", Number = 3 });
            list.Add(new Item { BatchName = "BOne", Number = 4 });
            list.Add(new Item { BatchName = "BTwo", Number = 5 });
            list.Add(new Item { BatchName = "BOne", Number = 5 });
            list.Add(new Item { BatchName = "BOne", Number = 7 });
            list.Add(new Item { BatchName = "BTwo", Number = 8 });
            list.Add(new Item { BatchName = "B", Number = 8 });

            Console.WriteLine("no order by: ");
            list.GroupBy(x => x.BatchName)
                .ToList()
                .ForEach(g => g.ToList().ForEach(i => Console.WriteLine(i)));

            Console.WriteLine("group order by key: ");
            list.GroupBy(x => x.BatchName)
                .OrderBy(g=>g.Key)
                .ToList()
                .ForEach(g => g.ToList().ForEach(i => Console.WriteLine(i)));


            Console.WriteLine("group order by key, item order by number ");
            list.GroupBy(x => x.BatchName)
                .OrderBy(g => g.Key)
                .ToList()
                .ForEach(g => g.OrderBy(i=>i.Number).ToList().ForEach(i => Console.WriteLine(i)));


            Console.WriteLine("done");
            Console.ReadKey();
        }
    }
}

```