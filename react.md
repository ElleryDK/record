## 父组件传递给子组件
```js
function Detail({content,active}){
  return (
    <>
      <p>{content}</p>
      <p>状态：{active?'选中':'没选中'}</p>
    </>
  )
}

function Article({title,articleDetail}){
  return (
    <div>
      <h2>{title}</h2>
      <Detail
      {...articleDetail}
      />
    </div>
  )
}

function App() {
  const articleData={
    title:"标题",
    articleDetail:{
      content:"内容",
      active:true
    }
  }
  return (
    <div className="App">
      <Article 
      {...articleData}
      />
    </div>
  );
}

export default App;

```

## 子组件传递给父组件 监听
```js
import { useState } from "react"

function Detail(onActive){
  const [status,setStaus] = useState(false) 
  function handleClick(){
    setStaus(!status)
    onActive(status)
  }
  return(
    <div>
      <button onClick={handleClick}>按钮</button>
      <p style={{
        display:status ?'block':'none'
      }}>
        内容
      </p>
    </div>
  )
}

function App() {
  function handleActive(status){
    console.log(status)
  }
  return (
    <div>
      <Detail
      onActive = {handleActive}
      />
      
    </div>
  );
}

export default App;

```

## 顶级数据
```js
const level = createContext(1)
```