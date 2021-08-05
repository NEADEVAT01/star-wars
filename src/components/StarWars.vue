<template>
  <transition name="popup" appear>
    <Popup v-if="isVisible" @click="isVisible=false">
      <p class="m-3 fs-2">{{ randomChars[openedChar].name }}</p>
      <img src="../assets/Char.jpg" alt="Charecter-1" class="w-75">
      <p class="m-3 fs-4">Height: {{ randomChars[openedChar].height }}</p>
      <p class="m-3 fs-4">Mass: {{ randomChars[openedChar].mass }}</p>
      <p class="m-3 fs-4">Hair color: {{ randomChars[openedChar].hair_color }}</p>
      <p class="m-3 fs-4">Skin color: {{ randomChars[openedChar].skin_color }}</p>
      <p class="m-3 fs-4">Eye color: {{ randomChars[openedChar].eye_color }}</p>
      <p class="m-3 fs-4">Birth year: {{ randomChars[openedChar].birth_year }}</p>
      <p class="m-3 fs-4">Gender: {{ randomChars[openedChar].gender }}</p>
    </Popup>
  </transition>


  <transition name="popup" appear>
    <Popup v-if="isVisibleShip" @click="isVisibleShip=false">
      <p class="m-3 fs-2">{{ randomShips[openedShip].name }}</p>
      <img src="../assets/Ship.jpg" alt="Charecter-1" class="w-75">
      <p class="m-3 fs-4">Model: {{ randomShips[openedShip].model}}</p>
      <p class="m-3 fs-4">Class: {{ randomShips[openedShip].vehicle_class}}</p>
      <p class="m-3 fs-4">Manufacturer: {{ randomShips[openedShip].manufacturer}}</p>
      <p class="m-3 fs-4">Length:{{ randomShips[openedShip].length}}</p>
      <p class="m-3 fs-4">Cost in credits: {{ randomShips[openedShip].cost_in_credits}}</p>
      <p class="m-3 fs-4">Crew{{ randomShips[openedShip].crew}}</p>
      <p class="m-3 fs-4">Passengers: {{ randomShips[openedShip].passengers}}</p>
      <p class="m-3 fs-4">Max Atmosphering Speed: {{ randomShips[openedShip].max_atmosphering_speed}}</p>

    </Popup>
  </transition>


  <transition name="popup" appear>
    <Popup v-if="isVisiblePlanet" @click="isVisiblePlanet=false">
      <p class="m-3 fs-2">{{ randomPlanets[openedPlanet].name }}</p>
      <img src="../assets/Planet.jpg" alt="Charecter-1" class="w-75">
      <p class="m-3 fs-4">Rotation period: {{ randomPlanets[openedPlanet].rotation_period}}</p>
      <p class="m-3 fs-4">Gravity: {{ randomPlanets[openedPlanet].gravity }}</p>
      <p class="m-3 fs-4">Population: {{ randomPlanets[openedPlanet].population }}</p>
      <p class="m-3 fs-4">Climate: {{ randomPlanets[openedPlanet].climate }}</p>
      <p class="m-3 fs-4">Terrain: {{ randomPlanets[openedPlanet].terrain }}</p>
    </Popup>
  </transition>


  <transition name="popup" appear>
    <Popup v-if="isVisibleSearch" @click="isVisibleSearch=false">
      <p class="m-3 fs-2">{{ searchResults[openedSearch].name }}</p>
      <img src="../assets/Char.jpg" alt="Charecter-1" class="w-75">
      <p class="m-3 fs-4">Height: {{ searchResults[openedSearch].height }}</p>
      <p class="m-3 fs-4">Mass: {{ searchResults[openedSearch].mass }}</p>
      <p class="m-3 fs-4">Hair color: {{ searchResults[openedSearch].hair_color }}</p>
      <p class="m-3 fs-4">Skin color: {{ searchResults[openedSearch].skin_color }}</p>
      <p class="m-3 fs-4">Eye color: {{ searchResults[openedSearch].eye_color }}</p>
      <p class="m-3 fs-4">Birth year: {{ searchResults[openedSearch].birth_year }}</p>
      <p class="m-3 fs-4">Gender: {{ searchResults[openedSearch].gender }}</p>
    </Popup>
  </transition>


  <header class="bg-dark">
    <a href="#"><img src="../assets/Star_Wars_Yellow.svg" alt="" class="logo m-2"></a>
    <div class="container">
      <input type="text" placeholder="Search" class=" w-25 p-1 m-3 form-control d-inline" v-model="searchRequest"
        v-on:keyup.enter="search">
      <button class="btn btn-warning" @click="search">Search</button></div>

  </header>


  <main>
    <div class="row m-5 justify-content-center" v-if="searchResults != ''">
      <h1>Search results "{{ searchRequest }}"</h1>
      <transition name="list" appear v-for="(item, index) in searchResults" :key="item.name">
        <div class="col-3" v-show="true" @click="isVisibleSearch=true, openedSearch=index">
          <p class="display-5">{{ item.name }}</p>
          <img src="../assets/Char.jpg" alt="Charecter" class="w-75">
        </div>
      </transition>
    </div>


    <div class="container-fluid p-0" v-if="searchResults == ''">


      <transition name="fade" appear>
        <h1 class="display-3" v-show="true">Charecters</h1>
      </transition>


      <div class="row m-5 justify-content-center">
        <transition name="list" appear v-for="(item, index) in randomChars" :key="item.name">
          <div class="col-3" v-show="true" @click="isVisible=true, openedChar=index">
            <p class="display-5">{{ item.name }}</p>
            <img src="../assets/Char.jpg" alt="Charecter" class="w-75">
          </div>
        </transition>
      </div>


      <div class="bg-dark text-white p-2">
        <transition name="fade" appear>
          <h2 class="display-3" v-show="true">Ships</h2>
        </transition>


        <div class="row m-5 justify-content-center">
          <transition name="list" appear v-for="(item, index) in randomShips" :key="item.name">
            <div class="col-3" v-show="true" @click="isVisibleShip=true, openedShip=index">
              <p class="display-5">{{item.name}}</p>
              <img src="../assets/Ship.jpg" alt="Charecter-1" class="w-75">
            </div>
          </transition>
        </div>


      </div>

      <transition name="fade" appear>
        <h3 class="display-3" v-show="true">Planets</h3>
      </transition>


      <div class="row m-5 justify-content-center">
        <transition name="list" appear v-for="(item, index) in randomPlanets" :key="item.name">
          <div class="col-3" v-show="true" @click="isVisiblePlanet=true,openedPlanet=index">
            <p class="display-5">{{item.name}}</p>
            <img src="../assets/Planet.jpg" alt="Charecter-1" class="w-75">
          </div>
        </transition>
      </div>

    </div>
  </main>
</template>

<script>
  import Popup from '../components/Popup.vue'

  export default {
    name: 'StarWars',
    components: {
      Popup
    },
    data() {
      return {
        isVisible: false,
        isVisibleShip: false,
        isVisiblePlanet: false,
        isVisibleSearch: false,
        Chars: [],
        Ships: [],
        Planets: [],
        openedChar: 0,
        openedShip: 0,
        openedPlanet: 0,
        openedSearch: 0,
        searchRequest: '',
        searchResults: ''

      }
    },
    computed: {
      randomChars: function () {
        let randChars = []
        for (let i = 0; i < 3; i++) {
          randChars.push(this.Chars[Math.floor(Math.random() * this.Chars.length)])
        }
        return randChars
      },
      randomShips: function () {
        let randShips = []
        for (let i = 0; i < 3; i++) {
          randShips.push(this.Ships[Math.floor(Math.random() * this.Ships.length)])
        }
        return randShips
      },
      randomPlanets: function () {
        let randPlanets = []
        for (let i = 0; i < 3; i++) {
          randPlanets.push(this.Planets[Math.floor(Math.random() * this.Planets.length)])
        }
        return randPlanets
      }
    },
    created: function () {
      fetch('http://swapi.dev/api/people/')
        .then(response => response.json())
        .then(data => {
          this.Chars = data.results
        })
      fetch('https://swapi.dev/api/planets/')
        .then(response => response.json())
        .then(data => {
          this.Planets = data.results
        })
      fetch('https://swapi.dev/api/starships/')
        .then(response => response.json())
        .then(data => {
          this.Ships = data.results
        })
    },
    methods: {
      search() {
        if (this.searchRequest == '') {
          console.log(1)
          this.searchResults = ''
          return 1
        }
        fetch('http://swapi.dev/api/people/?search=' + this.searchRequest)
          .then(response => response.json())
          .then(data => {
            this.searchResults = data.results
          })
        console.log(this.searchResults)

      }
    },
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1 {
    margin: 40px 0 0;
  }

  h2 {
    margin: 40px 0 0;
  }

  h3 {
    margin: 40px 0 0;
  }

  .col-3 {
    cursor: pointer;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 0 10px;
  }

  a {
    color: #42b983;
  }

  .logo {
    width: 10%;
  }

  input {
    height: 40px;
  }

  .btn-primary {
    height: 40px;
  }

  /*Animations*/

  .fade-enter-active,
  .popup-enter-active {
    transition: opacity .5s ease;
  }

  .fade-enter-from,
  .popup-enter-from,
  .list-enter-from {
    opacity: 0;
  }

  .list-enter-active {
    transition: opacity 1s ease;
  }

  .popup-leave-active {
    transition: all 1s;
    transform: translateY(-1000px);
    opacity: 0;
  }
</style>