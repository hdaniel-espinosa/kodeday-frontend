<template>
  <div id="app">
    <header class="header">
      <Navbar />
    </header>
    <section class="pets">
      {{ pets }}
      <template v-for="(pet,index) in pets">
        <Dog
        imageSrc="https://www.neoesfera.com/wp-content/uploads/2018/05/logo-perro.png"
        :name="pet.name"
        :age="pet.age"
        :gender="pet.gender"
        :breed="pet.breed"
        :key="index"
        :isAdopted="pet.isAdopted"
        :id="pet.id"
        />
      </template>
    </section>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue';
import Dog from './components/Dog.vue';

export default {
  name: 'app',
  components: {
    Navbar,
    Dog
  },
  async beforeMount() {
    const response = await fetch('https://dogapi-59p4hrc7v.now.sh/dogs')

    const data = await response.json();

    this.pets = data.payload.dogs;
    
  },
  data() {
    return {
      pets: []
    }
  }
}
</script>

<style src="./assets/index.css"></style>

<style scoped>
  #app {
    width: 100%;
    height: 100%;

    flex-direction: column;
  }
</style>