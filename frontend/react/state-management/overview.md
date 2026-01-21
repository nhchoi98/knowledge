# 상태관리

# Redux

## 핵심 키워드

Provider, Reducer, Context, `useSelector`, useDispatch, Thunk, Action, Redux toolkit, Slice, **`createEntityAdapter`**

[**Redux Toolkit**](https://redux-toolkit.js.org/) (also known as **"RTK"** for short) is our official recommended approach for writing Redux logic. The `@reduxjs/toolkit` package wraps around the core `redux`
 package, and contains API methods and common dependencies that we think
 are essential for building a Redux app. Redux Toolkit builds in our 
suggested best practices, simplifies most Redux tasks, prevents common 
mistakes, and makes it easier to write Redux applications.

**If you are writing *any* Redux logic today, you *should* be using Redux Toolkit to write that code!**

RTK includes utilities that help simplify many common use cases, including [store setup](https://redux-toolkit.js.org/api/configureStore),
[creating reducers and writing immutable update logic](https://redux-toolkit.js.org/api/createreducer),
and even [creating entire "slices" of state at once](https://redux-toolkit.js.org/api/createslice).

Whether you're a brand new Redux user setting up your first project, or an experienced user who wants to simplify an existing application, [**Redux Toolkit**](https://redux-toolkit.js.org/) can help you make your Redux code better.

Redux는 Flux 아키텍처 계열이야. 핵심 키워드를 짧게 정리하면 아래야.

### 1) Single Source of Truth (단일 상태 트리)

- 앱 전체 상태를 하나의 전역 스토어(store)에 넣는다.
- 즉, 상태가 여러 군데 흩어져서 누구 말이 맞는지 헷갈리지 않게 한다.
- 이걸로 "화면은 state의 함수다"라는 식의 사고가 가능해진다.

### 2) Store

- Redux의 중앙 상태 컨테이너.
- `getState()`로 현재 상태를 읽을 수 있고,
- `dispatch(action)`으로 상태 업데이트를 요청할 수 있고,
- `subscribe(listener)`로 상태 변화를 감지할 수 있다.
- React에선 `<Provider store={store}>`로 이 store를 내려준다.

### 3) State (상태)

- 지금 이 순간 앱이 가지고 있는 데이터 스냅샷.
- 예: `todos`, `isLoading`, `currentUser`, `page`, 등등.
- Redux에서는 state를 직접 바꾸면 안 되고 반드시 액션을 통해서만 바꾼다.
- 상태는 read-only 값

### 4) Action (액션)

- "무슨 일이 일어났는지"를 설명하는 순수 객체.
- `{ type: 'ADD_TODO', payload: { text: '빨래하기' } }` 이런 식.
- 액션은 그냥 사실 보고서다. "유저가 todo 추가를 눌렀다" 같은 사건의 선언.
- Naming convention: `domain/eventName`
- action의 payload는 description을 작성하는 곳이라고 보면 됨

### 5) Dispatch (디스패치)

- 액션을 스토어에 전달하는 함수.
- `dispatch(addTodo({ text: '빨래하기' }))`
- 디스패치하면 스토어는 리듀서를 돌려서 새로운 state를 만든다.

### 6) Reducer (리듀서)

- `(state, action) => newState` 형태의 순수 함수.
- 현재 상태와 액션을 받아서 다음 상태를 계산한다.
- You can think of a reducer as an event listener which handles events based on the received action (event) type.
- 중요한 점:
    - 기존 state를 "직접" 바꾸지 말고, 바뀐 복사본을 만들어서 리턴해야 한다.
    - Redux Toolkit은 immer를 써서 이걸 편하게 해준다.
        
        (겉보기엔 mutate처럼 써도 결국 불변 업데이트가 된다.)
        
    
- reducer는 아래의 하이어라키 구조 하위에 존재하는것을 권장함

**We recommend organizing your Redux app folders and files based on "features"**

### 7) Immutability (불변성)

- 상태는 직접 덮어쓰지 말고 복제 후 수정한 새 객체를 만들어야 한다.
- 이렇게 해야 React가 "아 상태 바뀌었네"라고 감지할 수 있고, time-travel 디버깅 같은 것도 가능해진다.
- Redux Toolkit은 이걸 자동으로 안전하게 해 줘서, 사실상 "불변성 유지"는 RTK 쓰면 기본 옵션처럼 따라온다.

### 8) Selector (셀렉터)

- `state.todo.todos`처럼 바로 접근해도 되지만, 규모가 커지면 `selectTodos(state)` 같은 셀렉터 함수를 따로 두고 재사용한다.
    - 스토어에서 원하는 조각만 뽑아오는 함수.
- React에서는 `useSelector(selectorFn)`로 사용한다.

### 9) Slice (Redux Toolkit에서 중요)

- 특정 도메인(예: todo, user, cart) 상태 + 액션 + 리듀서를 한 파일에 모아둔 단위.
- `createSlice({ name, initialState, reducers: { ... } })`로 정의.
- slice를 쓰면 액션 타입, 액션 생성자, 리듀서가 한 번에 나온다.
- 이게 RTK가 Redux 개발을 훨씬 덜 귀찮게 만든 핵심 포인트.
- A "slice" is a collection of Redux reducer logic and actions for a single feature in your app

### 10) Middleware (미들웨어)

- 디스패치 흐름 중간에 끼어드는 함수.
- 예: 비동기 처리 (redux-thunk), 로깅, 에러 리포팅.
- 액션이 리듀서에 도달하기 전에 가로채서 추가 작업을 할 수 있다.
- RTK의 `configureStore`는 thunk를 기본으로 깔아준다.
    
    그래서 그냥 `dispatch(async (dispatch, getState) => { ... })` 패턴도 가능하다.
    

### 11) UseDispatch

 the component will re-render any time the value returned from `useAppSelector` changes to a new reference.

---

## 정리

- Redux는 "상태를 전역 단일 스토어에서 관리하고, 상태 변경은 액션을 dispatch해서 리듀서가 계산한다"라는 규율을 강하게 깐다.
- 이 규율 덕분에 상태 흐름이 예측 가능하고 디버깅이 쉬워진다.
- 현대 Redux는 거의 항상 Redux Toolkit(createSlice, configureStore, immer 내장)으로 쓴다.
- Todo List 예제를 보면 흐름이 똑같다:
    1. 유저가 입력 → `dispatch(addTodo(...))`
    2. slice 리듀서가 state를 업데이트
    3. 컴포넌트는 `useSelector`로 새 state를 다시 그린다

이 패턴이 곧 Flux 스타일 단방향 데이터 흐름이야.

## Store구성

Redux는 하나의 스토어 사용을 권장하며, 여러 개의 상태는 하나의 스토어 내에서

```
combineReducers
```

(혹은

```
configureStore
```

의

```
reducer
```

옵션)를 사용하여 여러 개의 리듀서(slice)를 합쳐서 관리합니다. 여러 개의 스토어를 만들면 복잡성이 증가하므로, 일반적으로는 하나의 스토어를 유지하며 필요에 따라 스토어 안에 여러 개의 슬라이스를 두는 방식으로 구현합니다.

주요 개념

- **하나의 스토어:** 각 애플리케이션에는 단 하나의 Redux 스토어가 존재하는 것이 일반적입니다.
- **여러 개의 리듀서 합치기:** 애플리케이션에 여러 기능(상태)이 필요하다면, 각각의 리듀서를 `combineReducers` 함수로 합쳐 하나의 스토어가 관리하도록 합니다.
- **Redux Toolkit에서의 슬라이스:** Redux Toolkit을 사용하면 `createSlice`로 여러 개의 슬라이스를 만들고, 이를 `configureStore`의 `reducer` 옵션에 전달하여 하나의 스토어에 등록합니다.

링크: [https://nayah.tistory.com/139](https://nayah.tistory.com/139)

## Thunk

"thunk" is a programming term that means ["a piece of code that does some delayed work"](https://en.wikipedia.org/wiki/Thunk).

일반적으로 reducer는 sync function만 사용가능하다.

그래서 API에서 데이터를 불러오는 기능을 reducer로 구현하려고 하면 구현할 수 없다. (API에서 데이터를 불러오기 위해서는 asyncronous하게 구현해야하기 때문)

이를 위해 제공되는 것이 `createAsyncThunk` 이다.

`createAsyncThunk`는 action type과 콜백 함수를 받아 Promise를 반환하는 함수이다.

> **Why Client Components?**
> 
> 
> Any component that interacts with the Redux store (creating it, providing it, reading from it, or writing to it) needs to be a client component. This is because **accessing the store requires React context, and context is only available in client components.**
> 

## 비동기 처리 및 구성

### 핵심 keyword

Thunk, middleware, action, slice, state 

"thunk" is a programming term that means ["a piece of code that does some delayed work"](https://en.wikipedia.org/wiki/Thunk).

이를 위해 제공되는 것이 `createAsyncThunk` 이다.

`createAsyncThunk`는 action type과 콜백 함수를 받아 Promise를 반환하는 함수이다.

# Recoil

[Redux 설계 프롬프트 ](%EC%83%81%ED%83%9C%EA%B4%80%EB%A6%AC/Redux%20%EC%84%A4%EA%B3%84%20%ED%94%84%EB%A1%AC%ED%94%84%ED%8A%B8%2029acee38e89a807a886ad5a19941fc12.md)