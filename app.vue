<template>
  <div>
    <header>
      <h1> {{ zelda.data.monsters[0].name }} </h1>
      <img :src ="zelda.data.monsters[0].image" alt="">
      <p> {{ zelda.data.monsters[0].description }} </p>
      
      <p> Drops: </p>
      <ul>
        <li v-for="x in zelda.data.monsters[0].drops" :key="x">
          {{x}}
        </li>
      </ul>

      <p> Common Locations: </p>
      <ul>
        <li v-for="x in zelda.data.monsters[0].common_locations" :key="x">
          {{x}}
        </li>
      </ul>
    </header>
  </div>
</template>

<script setup>
  const { data: zelda } = await useFetch('https://botw-compendium.herokuapp.com/api/v2')
  console.log (zelda.value.data.monsters[0])
</script>