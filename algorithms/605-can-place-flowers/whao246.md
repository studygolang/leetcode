### 605. 种花问题


### 代码
```
func canPlaceFlowers(flowerbed []int, n int) bool {
	count:=0

	for i:=0;i<len(flowerbed);i++{
		if n==0{
			return true
		}
		if flowerbed[i]==0{
			if len(flowerbed)==1{
				return true
			}
			if i==0&&flowerbed[i+1]==0{
				flowerbed[0]=1
				count++
			}
			if i==len(flowerbed)-1&&flowerbed[i-1]==0{
				flowerbed[0]=1
				count++
			}
			if i>0&&i<len(flowerbed)-1&&flowerbed[i-1]==0&&flowerbed[i+1]==0{
				flowerbed[i]=1
				count++
			}
		}
	}
	if count>=n{
		return true
	}
	return false
}
```