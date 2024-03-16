## 3.1 模块

### Angular项目启动过程分析

- `angular.json`：NG 项目的配置

  - `index`：`./src/index.html`      `<app-root></app-root>`
  - `brower`：`./scr/main.ts`

- `main.ts`：`bootstrapModule(AppModule)`

- `app.module.ts`：bootstrap：`AppComponent`

- `app.component.ts` ：`selector:'app-root'`

  ​                                 `templateUrl:'app.component.html`

- `app.component.html`：HTML片段

<img src="https://cdn.jsdelivr.net/gh/techniquenotes/photohouse/Angular202403162223408.png" alt="image-20240316134327607" style="zoom:50%;" />

## 3.2 组件

### Angular 核心概念（一）：模块

- Module：不同于Node.js 或 ES6中的模块，NG 中的模块就是一个抽象的容器，用于对组件进行分组。
- 整个应用初始时有且只有一个主组件：AppModule

### Angular 核心概念（二）：组件

- 组件：是一段可以反复使用的页面片段，如页头、轮播、手风琴
- 组件（Component）包括：模板（Template），脚本（Script），样式（Style）
- NG中任何一个组件必须申明在模块中

#### 自定义组件步骤

##### 创建组件

- 新建 `./app/myc01.ts`

```tsx
import {Component} from "@angular/core";
//装饰器（Decorator）--用于指定class的用途
@Component({
  template: '<h2>我的组件C01</h2><hr>',
  selector: 'myc01' //当做元素使用
})
export class MyC01Component{

}
```

##### 在某个模块中注册组件class：./app/app.module.ts

```tsx
@NgModule({
  declarations: [
    AppComponent,
    MyC01Component
  ],
  imports: [
    BrowserModule,
    AppRoutingModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

##### 使用已经注册过的组件：`appcomponent.html`

其他模板中可以调用组件

```html
<h1>我的Angular项目01</h1>
<hr>
<myc01></myc01>
```

<img src="https://cdn.jsdelivr.net/gh/techniquenotes/photohouse/Angular202403162223409.png" alt="image-20240316153448740" style="zoom:50%;" />

### 创建一个自定义组件 `myc02`

#### myc02.component.ts

```ts
import {Component} from "@angular/core";

@Component({
  selector: 'app-myc02',
  templateUrl: './myc02.component.html',
  styleUrls: ['./myc02.component.css']
})
export class Myc02Component{

}
```

#### 创建 myc02.component.html 

```html
<h2 class="succ">我的组件C02</h2>
<hr>
```

#### 创建 myc02.component.css

```css
h2{
  font-style: italic;
}

.succ{
  color: #383;
}
```

#### 注册到模块：app.module.ts

```ts
@NgModule({
  declarations: [
    AppComponent,
    MyC01Component,
    Myc02Component,
  ],
  imports: [
    BrowserModule,
    AppRoutingModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

#### 使用创建的组件：app.component.html

可以在`app-root`中调用，但不能自己调用自己（浏览器崩溃，栈溢出）

```html
<h1>我的Angular项目01</h1>
<hr>
<myc01></myc01>

<app-myc02></app-myc02>
```

<img src="https://cdn.jsdelivr.net/gh/techniquenotes/photohouse/Angular202403162222309.png" alt="image-20240316161246569" style="zoom:50%;" />

## 3.3 npm

- Angular 没有根标签个数限制
- 组件自己的css内的样式只能该组件自己使用

### 创建组件的简化工具

在当前项目根目录下执行

```java
D:\Angular_Learning\Project\myngapp01> ng g component myc04
CREATE src/app/myc04/myc04.component.html (21 bytes)
CREATE src/app/myc04/myc04.component.spec.ts (617 bytes)
CREATE src/app/myc04/myc04.component.ts (205 bytes)
CREATE src/app/myc04/myc04.component.css (0 bytes)
UPDATE src/app/app.module.ts (707 bytes)
```

<img src="https://cdn.jsdelivr.net/gh/techniquenotes/photohouse/Angular202403162223410.png" alt="image-20240316195003636" style="zoom:50%;" />

## 3.4 HTML绑定

Angular 核心概念（三）：数据绑定

- HTML 绑定：{{NG 表达式}}
- 属性绑定
- 指令绑定
- 事件绑定
- 双向数据绑定

HTML 绑定，NG表达式可以执行算术、比较、逻辑、三目运算，调用函数，不能创建对象、JSON序列化

### myc05.component.ts

```tsx
@Component({
  selector: 'app-myc05',
  templateUrl: './myc05.component.html',
  styleUrl: './myc05.component.css'
})
export class Myc05Component {
  uname = 'ding dang'
  age = 20
  protected readonly JSON = JSON;
}
```

### myc05.component.html

```html
<p>myc05 works!</p>
<hr>
<div>用户名：{{uname}}</div>
<div>年龄：{{age}}</div>
<div>后年年龄：{{age+2}}</div>
<div>成年了吗：{{age>=18}}</div>
<div>成年了吗：{{age>=18?'成年':'未成年'}}</div>
<div>在法定工作年龄吗：{{age>=18 && age<60}}</div>
<div>用户名长度：{{uname.length}}</div>
<div>用户名大写形式：{{uname.toUpperCase()}}</div>
<div>用户名中下标为2的字符：{{uname[2]}}</div>
<!-- 不能创建对象 <div>当前时间：{{new Date()}}</div-->
<!--<div>JSON字符串：{{JSON.stringify({})}}</div>-->
```

<img src="https://cdn.jsdelivr.net/gh/techniquenotes/photohouse/Angular202403162223412.png" alt="image-20240316201347228" style="zoom: 67%;" />

## 3.5 属性绑定

### myc05.component.html

```html
<!--形式1-->
<p title="{{uname}}">asjhfjsnfjsh</p>
<!--形式2-->
<p [title]="uname">asjhfjsnfjsh</p>
```

![image-20240316202457851](https://cdn.jsdelivr.net/gh/techniquenotes/photohouse/Angular202403162223413.png)



