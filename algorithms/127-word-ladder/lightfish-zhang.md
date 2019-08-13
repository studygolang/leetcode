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