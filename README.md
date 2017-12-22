static void Main(string[] args)
        {
            var cache = CacheFactory.Build(
                "getStartedCache",
                settings => { settings.WithSystemRuntimeCacheHandle("handleName"); });

            cache.Add("keyA", "valueA");
            cache.Put("keyB", 23);
            cache.Update("keyB", v => 42);

            Console.WriteLine("KeyA is " + cache.Get("keyA")); // should be valueA
            Console.WriteLine("KeyB is " + cache.Get("keyB")); // should be 42
            cache.Remove("keyA");

            Console.WriteLine("KeyA removed? " + (cache.Get("keyA") == null).ToString());

            Console.WriteLine("We are done...");
            Console.ReadKey();
        }
