<script>
  import { each } from "svelte/internal";

  let count = 0;
  const handleClick = () => {
    count += 1;
  };

  // $: 로 선언된 변수는 참조하는 상태값이 변경될 경우에 이를 감지해 자동으로 함께 변경된다.
  $: doubled = count * 2;
  $: {
    console.log("count : ", count);
    console.log("doubled : ", doubled);
  }

  $: if (count >= 10) {
    alert("카운트가 10을 넘었어요.");
    count = 9;
  }

  let people = {
    name: "ty",
    age: 20,
    cat: true,
  };

  let list = [
    {
      id: 0,
      content: "first todo",
      done: false,
    },
    {
      id: 1,
      content: "2 todo",
      done: true,
    },
    {
      id: 2,
      content: "3 todo",
      done: true,
    },
    {
      id: 3,
      content: "4 todo",
      done: false,
    },
  ];

  const handleAddTodo = () => {
    const todo = {
      id: list.length + 1,
      content: "new Todo",
      done: false,
    };
    // // list 재할당 해줘야 component에 반영된다.
    // list.push(todo);
    // list = list;

    // 스프레드 연산자를 쓰면 좀 더 직관적으로 볼 수 있다.
    list = [...list, todo];
  };
</script>

<h3>footer Space</h3>
<div>
  <button on:click={handleClick}
    >click : {count} {count > 1 ? "times" : "time"}</button
  >
  <div>Count : {count}</div>
  <div>Name : {people.name}</div>
  <div>Age : {people.age}</div>
  <div>Cat : {people.cat}</div>
</div>

<button on:click={handleAddTodo}>Add</button>
<ul>
  {#each list as item}
    <li>
      <p>{item.id}</p>
      <p>{item.content}</p>
      <p>{item.done}</p>
    </li>
  {/each}
</ul>
