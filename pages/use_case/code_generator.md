---
layout: iframe-left
url: https://www.youtube.com/embed/4Pbx0j2Q_qI?si=t9pSfZXHvqfItvhG
---

# How to use ChatGPT to generate a code?

<div v-click>
- 使用提示詞：
</div>
<div v-click>
```markdown
請給我一份簡單計算機功能的 Python 腳本
```
</div>
<div v-click>
- 結果：
</div>
<div v-click>
```python
def main():
    print("簡單計算機:")
    num1 = float(input("輸入第一個數字: "))
    op = input("輸入運算符 (+, -, *, /): ")
    num2 = float(input("輸入第二個數字: "))

    if op == '+':
        print("結果:", num1 + num2)
    elif op == '-':
        print("結果:", num1 - num2)
    elif op == '*':
        print("結果:", num1 * num2)
    elif op == '/':
        if num2 == 0:
            print("錯誤: 除數不能為0")
        else:
            print("結果:", num1 / num2)
    else:
        print("無效的運算符")

if __name__ == "__main__":
    main()
```
</div>