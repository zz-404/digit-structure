# 栈的特性
- 可以实现配对相消，如果这样的话后面就不会再看到这一项
- 只有两个操作入和出，可以作为判断符合栈序列是否合法的条件

```
题目描述
将中缀表达式（infix expression）转换为后缀表达式（postfix expression）。假设中缀表达式中的操作数均以单个英文字母表示，且其中只包含左括号'('，右括号‘)’和双目算术操作符+，-，*， /。

输入描述
表示中缀表达式的一个字符串（其中只包含操作数和操作符和左右括号，不包含任何其他字符），长度不超过100个字符。

输出描述
对应后缀表达式字符串（其中只包含操作数和操作符，不包含任何其他字符）

样例输入
A+B*C-D-E/F

a+(b-c)*d+e/f

样例输出
ABC*+D-EF/-

abc-d*+ef/+


#include<iostream>
#include<stack>
using namespace std;

//栈的特性，匹配之后配对之后消去后面就不会再注意到这个项
//加减负责清空前面到括号处的一整项，这样的话乘除就是先被清空的，
//反括号和正括号负责清空内部项
int main(){
    string a;
    cin>>a;
    string ans="";
    stack<char> tok;
    int flag=0;
    for(int i=0;i<a.length();i++){

        if(a[i]=='('){
            tok.push(a[i]);
            flag++;
        }else if(a[i]==')'){
            while(tok.top()!='('){
                ans+=tok.top();
                tok.pop();
            }
            tok.pop();
            flag--;
        }else if(a[i]>='A'&&a[i]<='Z'||a[i]>='a'&&a[i]<='z'){
            ans+=a[i];
        }else if(a[i]=='*'||a[i]=='/'){
            tok.push(a[i]);
        }else if(a[i]=='+'||a[i]=='-'){
            while(!tok.empty()){
                if(tok.top()=='('){
                    break;
                }else{
                    ans+=tok.top();
                    tok.pop();
                }    
            }
            tok.push(a[i]);
        }
        // if(i==0){
        //     ans+=a[i];
        // }
        // else if((a[i]>='A'&&a[i]<='Z'||a[i]>='a'&&a[i]<='z')&&i-1>=0&&a[i-1]!='*'&&a[i-1]!='/'){
        //     ans+=a[i];
        // }
        // else if(a[i]=='+'||a[i]=='-'){
        //     tok.push(a[i]);
        // }else if(a[i]=='*'||a[i]=='/'){
        //     ans+=a[i+1];
        //     tok.push(a[i]);
        //     while(!tok.empty()){
        //         ans+=tok.top();
        //         tok.pop();
        //     }
        // }else if(a[i]==')'){
        //     ans+=tok.top();
        //     tok.pop();
        // }
    }
    while(!tok.empty()){
        ans+=tok.top();
        tok.pop();
    }
    cout<<ans;
}
```
