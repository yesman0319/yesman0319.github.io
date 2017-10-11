---
title: if(-1) return ture;
---
## 当if条件为负数的时候
在使用indexOf字符串查询的时候，返回了-1；导致if判断错误，这个错误已经犯下2次了。这次赶紧记一下。

	//举个栗子:
	if(-1){
		console.log("-1 is true")
	}else{
		console.log("-1 is false")
	}
	//输出结果 为 -1 is true
然后又去文档上查了一下

	//If 语句
	//只有当指定条件为 true 时，该语句才会执行代码。

综上所得：if判断，当条件为负数时，为真！


