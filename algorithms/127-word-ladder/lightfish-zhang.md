# 127.Word Ladder

## 解法

广度优先搜索，从第一单词开始，每个位置上的字母都修改一次26个字母，得出第一步的所有可能性（判断是否在字典中），第二步在第一步的所有可能性上再重复第一步，相当于每一条路都执行一步（每个单词修改一个字母的可能性），这样，以最短步骤找到终点单词

```golang

func ladderLength(beginWord string, endWord string, wordList []string) int {
	wordSet := map[string]bool{}
	for _, word := range wordList {
		wordSet[word] = true
	}
	if !wordSet[endWord] {
		return 0
	}
	var res int = 0
	queue := []string{beginWord}
	for len(queue) > 0 {
		for i := len(queue); i > 0; i-- {
			word := queue[0]
			queue = queue[1:]
			if word == endWord {
				return res + 1
			}
			for j := 0; j < len(word); j++ {
				newByte := []rune(word)
				var ch rune
				for ch = 'a'; ch <= 'z'; ch++ {
					newByte[j] = ch
					newWord := string(newByte)
					if wordSet[newWord] && newWord != word {
						queue = append(queue, newWord)
						delete(wordSet, newWord)
					}
				}
			}
		}
		res++
	}
	return 0
}
```

上面是单向的广度优先搜索的解法，由于题目是有起点与终点，可以双向搜索，同时从起点与终点搜索 

```golang
func ladderLength(beginWord string, endWord string, wordList []string) int {
	wordSet := map[string]bool{}
	for _, word := range wordList {
		wordSet[word] = true
	}
	if !wordSet[endWord] {
		return 0
	}
	var wl int = len(beginWord)
	var step int = 0
	q1 := map[string]bool{beginWord: true}
	q2 := map[string]bool{endWord: true}
	for len(q1) > 0 && len(q2) > 0 {
		step++
		if len(q1) > len(q2) {
			q1, q2 = q2, q1
		}
		q := map[string]bool{}
		for w, _ := range q1 {
			for i := 0; i < wl; i++ {
				chars := []rune(w)
				for j := 'a'; j <= 'z'; j++ {
					chars[i] = j
					newWord := string(chars)
					if q2[newWord] {
						return step + 1
					}
					if !wordSet[newWord] {
						continue
					}
					delete(wordSet, newWord)
					q[newWord] = true
				}
			}
		}
		q, q1 = q1, q
	}
	return 0
}
```