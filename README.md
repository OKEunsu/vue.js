# vue3-project
### Vue.js는 웹프론트엔드 프레임워크 입니다.

- 컴포넌트(Component) 기반의 SPA(Single Page Application)를 구축할 수 있게 해주는 프레임워크

### 컴포넌트(Component)

- 웹을 구성하는 로고, 메뉴바, 버튼, 모달창 등 웹 페이지 내의 다양한 UI 요소
- 재사용 가능하도록 구조화 한 것

### SPA(Single Page Application)

- 단일 페이지 어플리케이션
- 하나의 페이지 안에서 필요한 영역 부분만 로딩 되는 형태
- 빠른 페이지 변환
- 적은 트래픽 양

### Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```
### Vue istall
```
npm install -g @vue/cli
```

### 프로젝트 생성
```
vue create 프로젝트명
```

template : HTML
script : JS
style : CSS

### vue router 설치
```
npm install vue-router —save
```
  
### bootstrap vue 설치
```
npm install vue bootstrap bootstrap-vue
```

### 데이터 바이딩

속성 안에는 :속성="데이터이름"
문법 {{ 데이터 이름 }}

### Vue의 HTML 반복문

<태그 v-for="작명 in 몇회"> :key="작명"

### 이벤트

<butten @click = "데이터이름"></button>
<butten @mouseover = "데이터이름"></button>

### 함수

methods : {함수(){}}
함수안에서 데이터 쓸 땐 this.데이터명
```
<script>
import {ref} from 'vue'; 
export default{
  setup() {
    const name = ref('Kossie Coder1'); // ref을 이용하면 바뀐값이 적용할 수 있다, ref는 value를 써야한다. -> object, value만 가능!
    
    const updateName = () =>{
      name.value = 'Kossie Coder';
      console.log(name);
    }
    return {
      name,
      updateName
    };
  }
}
</script>
```
```
<script>
import {reactive} from 'vue'; // reactive 
export default{
  setup() {
    const name = reactive({"id" : 1}); // name.id로 변경이 가능하다. 
    
    const updateName = () =>{
      name.id = 2;
      console.log(name);
    }
    return {
      name,
      updateName
    };
  }
}
</script>
```
  
### 동적인 UI만드는 법

1. UI의 현재 상태를 데이터로 저장해둠
2. 데이터에 따라 UI가 어떻게 보일지 작성

### import / export 문법 쓰는법1

1. export default 변수명
2. import 변수명 from 그파일 경로

### import / export 문법 쓰는법2

1. export{변수1, 변수2..}
2. import{변수1} from 경로

HTML 태그안의 속성 데이터바인딩은 :어쩌구
HTML 태그안의 내용 데이터바인등은 {{어쩌구}}

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

### 축약
> v-bind -> :  
> v-on -> @

### v-model(양방향 데이터 바인딩)
```
<template>
  <input
    type='text' 
    v-model="name" 
  >
  <button 
    class = 'btn btn-primary' 
  @click="onSubmit">
    Click
  </button>
</template>

<script>
import {ref} from 'vue';

export default{
  setup() {
    const name = ref('Kossie');
            
    const onSubmit = () =>{
      console.log(name.value)
    }
    
    return {
      name,
      onSubmit,
    };
  }
}
</script>
```
Event Modifiers
- .stop
- .prevent
- .capture
- .self
- .once
- .passive

```
<template>
  <div class = 'container'>
    <h2>To-Do List</h2>
    <form class="d-flex" @submit.prevent="onSubmit">
      <div class ='flex-grow-1'>
        <input
        class="form-control mr-2"
        type='text' 
        v-model="todo" 
        placeholder = 'Type new to-do'
      >
      </div>
      <div>
        <button 
          class = 'btn btn-primary' 
        @click="onSubmit"
        type = "submit">
          Add
        </button>
      </div>
    </form>
    {{ todos }}
  </div>  
</template>

<script>
import {ref} from 'vue';

export default{
  setup() {
    const todo = ref('');
    const todos = ref([]);
            
    const onSubmit = () =>{
        todos.value.push({
        id : Date.now(),
        subject: todo.value
      });
    }
    
    return {
      todo,
      todos,
      onSubmit,
    };
  }
}
</script>
```
