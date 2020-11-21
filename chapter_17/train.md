# 第十七章练习题

## 第1题

```text
Y <- X
---------------
Y <- 0
TEMP <- 0
while(X)
{
    decr(X)
    incr(TEMP)
    incr(Y)
}
while(TEMP)
{
    decr(TEMP)
    incr(X)
}
```

## 第2题

```text
Z <- X + Y
---------------
Z <- X
TEMP <- Y
while(TEMP)
{
    incr(Z)
    decr(TEMP)
}
```

## 第3题

```text
Z <- Y * X
---------------
Z <- 0
TEMP <- Y
while(TEMP)
{
    decr(TEMP)
    Z <- Z + X
}
```

## 第4题

```text
Z <- Y ^ X
---------------
Z <- 0
incr(Z)
TEMP <- X
while(TEMP)
{
    decr(TEMP)
    Z <- Z * Y
}
```

## 第5题

```text
Y <- Y - X
---------------
while(X)
{
    decr(X)
    decr(Y)
}
```

## 第6题

```text
if (X) then
{
    A1
}
else
{
    A2
}
---------------
TEMP <- 0
incr(TEMP)
TEMP <- TEMP - X
while(X)
{
    decr(X)
    A1
}
while(TEMP)
{
    decr(TEMP)
    A2
}
```

## 第7题

```text
    |
... b 1 1 1 b ...
```

## 第8题

```text
      |
... b 1 1 1 b ...
```

## 第9题

该指令集不会停机

## 第10题

这里假定读/写头指向的第一位为空，第二位为二进制数的最低位，第三位为二进制数的次低位，以此类推。

状态机如下所示，其中S4为停机

![](../.gitbook/assets/4%20%283%29.png)

## 第11题

```text
    |
... b b b ...
```

```text
      |
... b b b ...
```

```text
    |
... b 1 b ...
```

```text
    |
... b 1 b ...
```

## 第12题

```text
    |
... b b b ...
```

```text
      |
... b b b ...
```

```text
      |
... b b b ...
```

## 第13题

![](../.gitbook/assets/5%20%282%29.png)

## 第14题

![](../.gitbook/assets/6%20%282%29.png)

```text
while(X)
{
    decr(X)
}
```

## 第15题

![](../.gitbook/assets/7%20%281%29.png)

```text
while(Y)
{
    decr(Y)
}
while(X)
{
    decr(X)
    incr(Y)
}
```

## 第16题

n+1个1

## 第17题

```text
X1 <- 0
---------------
while(X1)
{
    decr(X1)
}
---------------
CF1DBF1E -> 3474833182
```

## 第18题

```text
X2 <- 2
---------------
while(X2)
{
    decr(X2)
}
incr(X2)
incr(X2)
---------------
CF2DBF2EAF2AF2 -> 58315619324340980
```

## 第19题

```text
X3 <- X1 + X2
---------------
while(X3)
{
    decr(X3)
}
while(X1)
{
    decr(X1)
    incr(X3)
}
while(X2)
{
    decr(X2)
    incr(X3)
}
---------------
CF3DBF3ECF1DBF1AF3ECF2DBF2AF3E -> 1076057828720031022972054079850852158
```

