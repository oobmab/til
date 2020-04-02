# Markdown記法 まとめ

## header
### e.g.

```
# header
## header
### header
#### header
##### header
###### header
```
---

# header
## header
### header
#### header
##### header
###### header

---

## unordered-list
### e.g.

```
- parent-1
    - child-1
- parent-2
```
---
- parent-1
    - child-1
- parent-2
---

## ordered-list
### e.g.

```
1. parent-1
    1. child-1
    1. child-2
1. parent-2
1. parent-3
```
---
1. parent-1
   1. child-1
   2. child-2
2. parent-2
3. parent-3
---

## block-quotes
### e.g.

```
> Sample.
> 
> Sample.Sample.
```
---
> Sample.
> 
> Sample.Sample.
---

### e.g.
```
> Sample.  
> Sample.Sample.   
>> Sample.
>> 
>> Sample.Sample. 
```
---
> Sample.  
> Sample.Sample.   
>> Sample.
>> 
>> Sample.Sample. 
---

## pre-tag
### e.g.

```
    # Tab
    array(3) {
        [0]=>
        string(5) "test1"
        [1]=>
        string(5) "test2"
        [2]=>
        string(5) "test3"
    }
---
    # Space
    array(3) {
      [0]=>
      string(5) "test1"
      [1]=>
      string(5) "test2"
      [2]=>
      string(5) "test3"
    }

```
---
Tab

    array(3) {
        [0]=>
        string(5) "test1"
        [1]=>
        string(5) "test2"
        [2]=>
        string(5) "test3"
    }

Space

    array(3) {
        [0]=>
        string(5) "test1"
        [1]=>
        string(5) "test2"
        [2]=>
        string(5) "test3"
    }
---

## code-tag
### e.g.

```

`code`

```
---

`code`

---

## em-tag
### e.g.

```

plain *italic* plain
plain _italic_ plain

```
---

plain *italic* plain  
plain _italic_ plain

---

## strong-tag
### e.g.

```

plain **bold** plain
plain __bold__ plain

```

---

plain **bold** plain  
plain __bold__ plain

---

## hr-tag
### e.g.

```

***
___
---

```

## link
### e.g.

```

[Google](https://www.google.co.jp/)

```

---

[Google](https://www.google.co.jp/)

---

## definition-link
### e.g.

```
[google][google-link]

[google-link]: https://www.google.co.jp/

```

---

[Google][google-link]  

[google-link]: https://www.google.co.jp/  

---

## task-lists
### e.g.

```
- [ ] unchecked
- [x] checked
```
---

- [ ] unchecked
- [x] checked

---