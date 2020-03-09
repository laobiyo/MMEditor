# [MMEditor](https://tnt.tongdun.me/solution/mmEditorSolution)
* 基于Snap.svg绘图库完成的流程图框架，依赖少，开箱即用，提供dom接口方便对dom进行各种状态操作，demo 提供一个基础的数据流程demo 和 基础的流程项目 设计框架
* flow editor lib with snap.svg

# Demo

[tnt demo](https://tnt.tongdun.me/solution/mmEditorSolution)

# Install
```sh
npm i MMEditor --save
```

# Usage
```javascript
	import MMEditor from "MMEditor";
	
	let index = 0;
	const editor =  new MMEditor({ dom: document.getElementById("root")});
	// add node
	function add(){
		editor.graph.node.addNode({
			uuid:index,
			type:"default",
			name:"测试"+index++,
			x:window.innerWidth*Math.random(),
			y:300*Math.random()
		})
	}
	for(let x = 0;x<50;x++){
		add();
	}
	// add line
	for(let x = 0;x<10;x++){
		editor.graph.line.addLine({
			from:Math.floor(50*Math.random()),
			to:Math.floor(50*Math.random()),
			fromPoint:1,
			toPoint:0
		})
	}
	// result
	console.log(editor.schema.getData())
```

# registe node

```javascript
	import MMEditor from "MMEditor";
	
	let index = 0;
	const editor =  new MMEditor({ dom: document.getElementById("root")});
	// add node
	function add(){
		editor.graph.node.addNode({
			uuid:index,
			type:"file-node",
			name:"测试"+index++,
			x:window.innerWidth*Math.random(),
			y:300*Math.random()
		})
	} 
	// registe file-node
	editor.graph.node.registeNode("file-node", {
		linkPoints: [{ x: 0, y: 0.5 }, { x: 1, y: 0.5 }],
		render: (data, snapPaper) => {
			const node = snapPaper.rect(0, 0, 180, 30);
			const text = snapPaper.text(30, 20, data.name);
			const circle = snapPaper.circle(15, 15, 8).attr({fill: "#39a"});
			node.attr({
				fill: "#fff",
				stroke: "#000",
				rx: 5,
				ry: 5
			});
			return snapPaper.group(node, text, circle);
		}
	});
	add()
	// result data
	console.log(editor.schema.getData())
```

# Documention

[司南文档](https://sinan.tongdun.me/book/2035)


# Test
``` sh
npm i
npm run start
```
 