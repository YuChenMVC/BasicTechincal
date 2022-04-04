# 紀錄一些太久沒複習的觀念


## Static

以C++來說
<br>
static在建構子或不同地方所代表的意義也會不同
<br>
local的variable等同global
<br>
初始化只有一次 且只在{ }內有效
<br>
會活到記憶體裡的permanent被執行完
<br>
某些情況malloc()會引起嚴重記憶體洩漏問題
<br>
所以static能把他留下來又希望{}以外的其他程式別去碰他
<br><br>

舉例
```c++
void inc(){
    static int v = 0; //初始化只有一次
    v++;
    printf("v=%d\n",v);
}
int main(){
    inc();
    inc();
    inc(); //輸出結果為1,2,3...    
    return 0;
}
```
<br>


# Polymorphism

以C#來說
<br>
被父類別new出來的子類別, 就會以父類別的樣子表現出來
<br>

舉例

今天公司在徵工程師
```C#
public class BackEnd
{
    public string WriteJava()
    {
        // 要會寫 Java
    }    
}
```
有人來interview, 但面試太緊張
```C#
public class FirstTest : BackEnd
{
    public string WriteJava()
    {
        return "TooNervous";
    }
}
public void Test(){
    BackEnd test1 = new FirstTest();
}
```
不過筆試還勉強ok
<br>
```C#
public class SecondTest : BackEnd
{
    public string WriteJava()
    {
        return "Code";
    }
    public Photo TakePhoto()
    {
        return "除此之外他還會攝影";
    }
}
public void Test(){
    BackEnd test2 = new SecondTest();
}
```
通過面試開始上工後他就是要專心寫程式
```C#
public void FullTimeJob()
{
    BackEnd backend = new SecondTest();
    backend.WriteJava();
    backend.TakePhoto(); //喔對這個上班不能做
}
```

Ref. [菜雞與物件導向 (5): 多型](https://igouist.github.io/post/2020/07/oo-5-polymorphism/)


## std::sort()

swap()
```C++
template<class T>
void swap(T& a, T& b)
{
  T tmp(std::move(a));
  a = std::move(b);
  b = std::move(tmp);
}
```
C#和Java不能這樣寫
<br>
因為C#沒有Destructor,嚴格說起來工程師不能定義,是由Garbage Collector決定的
<br>

## Nested If Statement

Before
```c
int func(int input){
  if(input > 0){
    if(input < 18){
      printf("太瘦囉\n");
    }else if(input < 25){
      printf("完美體態\n");
    }else{
      printf("太胖囉\n");
    }
  }else{
    printf("輸入值不可為負數\n");
  }
}
```
After(暫不管single return law)
```c
int func(int input){
    if(input < 0){
        printf("輸入值不可為負數\n"); return 0;
    }
    if(input < 18){
        printf("太瘦囉\n"); return 0;
    }
    if(input < 25){
        printf("完美體態\n"); return 0;
    }
    printf("太胖囉");
}
```

## Resources

<br>
看完都不敢說會HelloWorld了
<br>
https://github.com/saturdayclass/hello-world-all-programming-language
<br>
工程師進化史
<br>
https://medium.com/@webseanhickey/the-evolution-of-a-software-engineer-db854689243


