##### Vue实现点击或者双击复制

###### 1.给div或者按钮绑定事件

`@dblclick="copyClipboard('HELLO WORLD')"`

###### 2.编码复制方法

```vue
copyClipboard (data) {
    if (data) {
		const copyContent = data
		// 创建input标签存放需要复制的文字
		const inputTag = document.createElement('input')
		// 把文字放进input中，供复制
		inputTag.value = copyContent
		document.body.appendChild(inputTag)
		// 选中创建的input
		inputTag.select()
		// 执行复制方法， 该方法返回bool类型的结果，告诉我们是否复制成功
		const copyResult = document.execCommand('copy')
		// 操作中完成后 从Dom中删除创建的input
		document.body.removeChild(inputTag)
		// 根据返回的复制结果 给用户不同的提示
		if (copyResult) {
			this.$message({
				message: '复制成功！',
				type: 'success'
			})
		} else {
			this.$message.error('复制失败！')
		}
	} else {
		this.$message.error('无内容！')
	}
}
```
