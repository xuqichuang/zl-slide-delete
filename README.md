# zl-slide-delete

> 臻旅左滑删除组件

## 引入组件

```
npm install zl-slide-delete -S
```

## 全局引用方法
> main.js 中引入

```
import zlSlideDelete from 'zl-slide-delete'
Vue.use(zlSlideDelete)
```

### zlSlideDelete
> 左滑删除，可以自定义滑动或不滑动，主要内容需根据组件需求而定义
> [臻旅所有组件地址](https://github.com/xuqichuang/zl-vue-ui)
###### 使用方法

> html
```
<zl-slide-delete 
  :options="dataList"
  @delete-item="deleteFn" 
  @editor="editorFn"/>
```
> js

```
data:{
dataList:[
    {
      id:1,
      title:'他大舅',
      content:[
        12,
        '臻旅科技你们的超级旅伴，机票酒店火车票火车票抢票景点'
      ]
    },
    {
      id:2,
      title:'他二舅',
      content:[
        15,
        '臻旅科技你们的超级旅伴，机票酒店火车票火车票抢票景点，臻旅科技你们的超级旅伴，机票酒店火车票火车票抢票景点'
      ]
    },
    {
      id:3,
      title:'都是他舅',
      content:[
        19,
        '臻旅科技你们的超级旅伴，机票酒店火车票火车票抢票景点'
      ]
    }
],// 数组里的content必须存在
}
methods:{
    editorFn(item){
      console.log(1,item)
    },
    deleteFn(index){
      this.dataList2.splice(index, 1)
    },
}
```
> props

```
options:{
  type:Array
},
left:{ //左侧编辑，删除选项
  type:String,
  default: 'none', //目前可选 'none', 'editor'
},
right:{
  type:String, //右侧选中，编辑选项
  default: 'none', //目前可选 'none', 'editor'
},
slideDelete:{ //true 可以左滑删除， false 不可以左滑删除， 默认true
  type:Boolean,
  default:true
},
editor:{ // 列表是否可编辑
  type:Boolean,
  default:true
},
leftImgOptions:{ // 左侧内容， 当left不为none显示
  type:Object,
  default(){
    return {
      img: require('./img/editor.png'),
      width: '20px',
      height: '20px'
    }
  }
},
rightImgOptions:{ // 右侧内容， 当right不为none显示
  type:Object,
  default(){
    return {
      img: require('./img/editor.png'),
      width: '20px',
      height: '20px'
    }
  }
}
```
> events

```
delete-item
返回值：
    index, Number // 删除的索引，
    item, Object //数组中的某一项
editor
返回值：
    item, Object // 数组中的某一项, 开发人员可以根据item 做编辑删除操作
```

