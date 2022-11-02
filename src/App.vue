<script setup>
import {ref,computed} from 'vue'
const products =ref([
 'Headphone',
 'Laptop',
 'TV',
 'Keybord',
 'Mouse'
])
const description = ref([
{
    id:1,
    img:'https://img.joomcdn.net/74277cb11c97d6f453c04ea4adb0e68c523e7857_1024_1024.jpeg',
    name:"Смартфон Apple",
    price:80,
  },
  {
    id:2,
    img:'keybord.jpeg',
    name:'Мембранная клавиатура',
    price:90,
  },
  {
    id:3,
    img:'laptop.jpeg',
    name:'Ноутбук',
    price:300,
  },
  {
    id:4,
    img:'tv.jpeg',
    name:'Телевизор',
    price:1190,
  },
  {
    id:5,
    img:'./assets/img/mouse.jpeg',
    name:'Светодиодная мышь',
    price:30,
  }
])



const query =ref('')

const queryProducts = computed(()=>{
  return products.value.filter((product)=>product.indexOf(query.value)!== -1)//Колбек функция
})
</script>

<template>
 <div class="container">
  <input  type="text"
   placeholder="Поиск товаров..."
   v-model="query">
   {{query}}
   <ul>
    <li
     v-for="product in queryProducts"
     :key="product">
      {{product}}
    </li>
   </ul>
 </div>
 <div class="description-product">
  <h1>Каталог</h1>
  <div class="card-1" v-for="descriptions in description"
  :key="descriptions.id"
  :description="descriptions">
    <img
                v-bind:src="this.description" 
                alt='Товар'
            />
   <li>{{descriptions.name}}</li>
   <li>{{descriptions.price}}$</li>
  </div>
 </div>
 
</template>

<style scoped>
.container{
  margin-left: auto;
    margin-right: auto;
    width: 700px;
    height: 400px;
  background: rgb(88, 84, 84);
  color: rgba(77, 153, 225, 0.956);
  align-items: center;
  font-size: 30px;
  border-radius: 15px;
  border: 1px solid rgb(121, 118, 118);
}
.container:hover{
  box-shadow:10px 10px rgb(76, 65, 50);
  transition: 0.6s ease-in-out;
}
input{
  width: 400px;
  height: 50px;
  border-radius: 20px;
}
li{
  list-style: none;
}
.description-product{
  display: flex;
  justify-content: center;
  
  width: 670px;
    height: 400px;
    background: rgb(88, 84, 84);
  color: rgba(77, 153, 225, 0.956);
 
  margin-left: auto;
    margin-right: auto;
    border-radius: 15px;
}
.card-1{
  width: 500px;
  height: 300px;
  border: 1px solid rgb(95, 81, 81);
  padding-top: 3em;
}
</style>
