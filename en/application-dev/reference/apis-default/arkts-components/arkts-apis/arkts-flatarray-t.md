# FlatArray

```TypeScript
type FlatArray<Arr, Depth extends number> = {
    "done": Arr,
    "recur": Arr extends ReadonlyArray<infer InnerArr>
        ? FlatArray<InnerArr, [-1, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20][Depth]>
        : Arr
}[Depth extends -1 ? "done" : "recur"]
```

**Type:** {
    "done": Arr,
    "recur": Arr extends ReadonlyArray&lt;infer InnerArr&gt;
        ? FlatArray&lt;InnerArr, [-1, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20][Depth]&gt;
        : Arr
}[Depth extends -1 ? "done" : "recur"]
