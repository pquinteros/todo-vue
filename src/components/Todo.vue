<template>
    <div id="todo-container">
        <div class="todo-title">
            Todo App
        </div>

        <div class="todo-subtitle">
            Please set up your shopping list so you can remember it later.
        </div>
        
        <div class="todo-forms">
            <input type="text" v-model="txtInput" v-on:keyup.enter="btnAdd" placeholder="Milk, Egg ...">
            <input type="button" value="Add" v-on:click="btnAdd">
        </div>

        <div class="todo-list" >
            <div class="item" v-for="(item,index) in items" v-bind:key="index">
                {{ item.text }} 
                <div @click="btnDelete(index)" class="delete">
                  <img src="../assets/delete.svg" alt="imagen">
                </div> 
                
            </div>
            
        </div>

    </div>
</template>

<script>
 

export default {
  name: 'Todo',
  props: {
    items:Object,
  },
  methods:{
       btnAdd: function () {
           if(this.txtInput){
           this.items.push({text:this.txtInput})
           this.txtInput='';
           }
       },

       btnDelete: function(index) {
           this.items.splice(index, 1);
       }

  }
}

</script>

<style>

:root{
--main-text: #292b2c;
--subtitle: #8a8d92;
--subtitle: #a1a4a8;
--placeholder: #b4bac4;
--border: #e4e9f3;
--accent: #2656ff;
--border-focus:#90aaff;
--bg-focus: #f2f5ff;
}
.todo-title{
    font-weight: 600;
    font-size: 18px;
    text-align: left;
    color: var(--main-text);
}

.todo-subtitle{
     color: var(--subtitle);
    font-size: 15px;
    padding: 15px 0;
}

#todo-container {
    background: white;
    width: 320px;
    padding: 30px;
    border-radius: 10px;
    box-shadow: 0 20px 40px 0 rgba(0, 0, 0, 0.1);
    border: 1px solid rgba(0, 0, 0, 0.1);
}

.todo-forms {
    display: flex;
    justify-content: space-between;
    padding: 15px 0;
}

input[type=text] {
    width: 62%;
    background: white;
    border: 2px solid var(--border);
    border-radius: 5px;
    padding: 15px;
    font-size: 14px;
}

input::placeholder {
color: var(--placeholder)!important;
opacity: 1 !important;
}

input[type=button] {
    display: flex;
    justify-content: center;
    width: 22%;
    background: white;
    border: 2px solid var(--border);
    border-radius: 5px;
    padding: 15px;
    font-size: 14px;
    font-weight: bold;
    background: white;
}

input[type=text]:focus{
    transition: border 1s ease-out;
    border: 2px solid var(--border-focus);
    background: var(--bg-focus) ;
}

input[type=button]:focus{
    transition: background 0.2s ease-out;
    border: 2px solid var(--border-focus);
    background: var(--bg-focus) ;

}

.todo-list{
    padding: 0 0 15px 0;
}

.item{
    color: var(--main-text);
    border-bottom: 1px solid var(--border);
    padding: 1px 16px 14px 16px;
    font-size: 14px;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    animation: slideUp 0.3s ease-out;
}

@keyframes slideUp {
  from {opacity: 0; }
  to {opacity: 1; }
}

.delete{
    transform: scale(0.5);
    transform-origin: bottom;
}

.delete:hover{
    opacity: 0.5;
}
</style>