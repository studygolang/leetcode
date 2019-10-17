利用栈的特性
```golang
func isValid(s string) bool {
	lenS := len(s)
	stack := make([]byte, lenS)
	top := 0 //头指针
	for i := 0; i < lenS; i++ {
		switch s[i] {
		case '(':
			stack[top] = '('
			top++
		case '[':
			stack[top] = '['
			top++
		case '{':
			stack[top] = '{'
			top++
		case ')':
			if top > 0 && stack[top-1] == '(' {
				top--
			} else {
				return false
			}
		case ']':
			if top > 0 && stack[top-1] == '[' {
				top--
			} else {
				return false
			}
		case '}':
			if top > 0 && stack[top-1] == '{' {
				top--
			} else {
				return false
			}
		}
	}
	return top == 0
}
```