## React中的生命周期函数
> 生命周期函数指在某一时刻组件会自动调用执行的函数

1. Initialization 初始化 
 ``` js
 // 在组件即将被挂载到页面的时候执行
 setup props and state
 ```
2. Mounting 挂载
 ``` js
   // 在组件即将被挂载到页面的时刻执行
   componentWillMount(){
    
   }
   
   // 渲染函数
   render(){
    
   }
   
   // 在组件已经被挂载到页面的时刻执行
   componentDidMount(){
   
   }
 
 ```
3. Updation 更新
 ``` js
   /* props */
   // 当一个组件从父组件接收了参数
   // 只要父组件的render函数被重新执行了，子组件的这个生命周期就会被执行
   // 如果这个组件第一次存在于父组件中，不会执行
   // 如果这个组件已经存在于父组件中，才会执行
   componentWillReceiveProps(){
    
   }
   
   // 组件被更新之前，会被自动执行
   shouldComponentUpdate(){
      return true; // 默认返回Boolean值， true为需要更新，false为不更新
   }
   
   // 组件被更新之前，会被自动执行。他在shouldComponentUpdate之后执行
   // 如果shouldComponentUpdate返回true它才执行
   // 如果shouldComponentUpdate返回false则不执行
   componentWillUpdate(){
   }
   
   render(){
   }
   
   // 组件更新完成之后会执行
   componentDidUpdate(){
   }
   
    /* states */
   shouldComponentUpdate(){
   }
   
   componentWillUpdate(){
   }
   
   render(){
   }
   
   componentDidUpdate(){
   }
 ```
4. Unmounting 卸载
 ``` js
 // 当组件即将从页面中删除的时候，会被执行
 componentWillUnmount(){
 
 }
 ```


