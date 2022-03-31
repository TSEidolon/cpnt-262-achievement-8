<template>
  <div>
    <header>
      <div class="header-content">
      <h1> The Legend of Zelda: Breath of The Wild - Random Monster Generator</h1>
      <button  @click="refresh"> Generate New Monster</button>
      </div>
    </header>
    <body>
      <section class="card-container-content">
      <div class="card-item">
        <h1 class="card-item-title"> {{ zelda.data.monsters[0].name }} </h1>
        <img :src ="zelda.data.monsters[0].image" :alt="zelda.data.monsters[0].name" class="card-item-image">
        <p class="card-item-text"> {{ zelda.data.monsters[0].description }} </p>
        <ul class="card-item-text">
          <p> Drops(if any): </p>
          <li v-for="x in zelda.data.monsters[0].drops" :key="x">
            {{x}}
          </li>
        </ul>
        <ul class="card-item-text">
          <p> Common Locations(if any): </p>
          <li v-for="x in zelda.data.monsters[0].common_locations" :key="x">
            {{x}}
          </li>
        </ul>
      </div> 
      </section>
    </body>
  </div>
</template>

<script setup>


const { data: zelda } = await useFetch('https://botw-compendium.herokuapp.com/api/v2')
console.log (zelda.value.data.monsters[0].name)

const refresh = () => refreshNuxtData() // leave this blank if your fetch has no key:id or else it won't work

</script>

<style>
.header-content{
  display:flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.header-content h1 {
  font-size: 2.5rem;
}
.header-content button {
  font-size: 2rem;
  background-color: rgba(128, 128, 128, 0.452);
  transition: all .5s ease-out;
  box-shadow: 0 2rem 4rem rgba(0, 0, 0, 0.2);
}
.header-content button:hover {
  background-color: rgba(128, 128, 128, 0.185);
  transform: translateY(-5%);
}
  .card-container-content {
  display: grid;
  grid-template-columns: repeat(auto, minmax(350px, 1fr));
  justify-items: center;

  
  }
  .card-item {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    width: 30%;

    padding: 1rem;


   border-radius: 10px;
   background-color: rgba(128, 128, 128, 0.39);
   box-shadow: 0 2rem 4rem rgba(0, 0, 0, 0.2);
   transition: all .5s ease-out;
  }

  .card-item:hover {
    transform: translateY(-.5%);
    box-shadow: 0 2rem 4rem rgba(0, 0, 0, 0.4);
  }

.card-item-image{
  object-fit: contain;
  width: auto, 50%;

}

.card-item-title{
  font-size: 3rem;
}

.card-item-text {
  font-size: 1rem;
}
</style>