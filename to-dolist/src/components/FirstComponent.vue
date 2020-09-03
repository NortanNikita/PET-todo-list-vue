<template>
  <div class="first-component">
      <div class="card"  v-for="(item, i) in items" :key="i" >
        <img :src="item.imgSrc" style="">
        <h3>Имя:{{item.name}}</h3>
        <p>Возраст:{{item.age}}</p>
        <p>Город:{{item.city}}</p>
        <button class="edit-btn" @click="testEdit(item)">Редактировать</button>
        <button class="delete-btn" @click="testDel(item.id)">x</button>
      </div>
  <div class="change-block">
      <div class="edit-block">
          <form v-if="selectedIndex != null">
            <h3>Редактирование</h3>
            <input type="text" v-model="items[selectedIndex].name" ><br>
            <input type="text" v-model="items[selectedIndex].age" ><br>
            <input type="text" v-model="items[selectedIndex].city" >
          </form>
      </div>

      <div class="add-block">
          
          <form >
            <h3>Добавление</h3>
            <input type="text" v-model="newObject.name"><br>
            <input type="text" v-model="newObject.age"><br>
            <input type="text" v-model="newObject.city"><br>
            <button class="add-btn" @click.prevent="testAdd()">Добавить</button>
          </form>
      </div>
  </div>
  </div>
  
</template>

<script>
export default {
 data: () => ({
  items: [
      { 
          id : 1,
          imgSrc: require('../assets/test-pic.png'),
          name: 'name 1',
          age: 'age',
          city: 'city'
      },
      {
          id : 2,
          imgSrc: require('../assets/test-pic.png'),
          name: 'name 2',
          age: 'age',
          city: 'city'
      },
      {   
          id : 3,
          imgSrc: require('../assets/test-pic.png'),
          name: 'name 3',
          age: 'age',
          city: 'city'
      },
  ], 
   newObject :{
      id : null,
      imgSrc: require('../assets/test-pic.png'),
      name: '',
      age: '',
      city: ''
  },
  selectedIndex: null
 }),
 methods:{
   testDel(id){
     this.selectedIndex = null
      for (var i=0; i < this.items.length; i++){
        if (id == this.items[i].id){
          this.items.splice(i,1);
        }
      }
   },
   testEdit(el){
      //  for (var i=0; i < this.items.length; i++){
      //   if (id == this.items[i].id){
      //     this.selectedIndex = i     
      //   }
      // } 

      this.selectedIndex = this.items.indexOf(el)
   },
   testAdd(){ 
     const random = Math.random() * 1000
     this.newObject.id = random
    this.items.push(this.newObject)
    this.newObject.id = null
  }
 }
}
</script>

