//<script setup>
import { ref, computed } from 'vue';

const superheroes = ref([ {
    nombre: "Superweed",
    descripcion: "Superman (en español: Superhombre) es un superhéroe ficticio que apareció por primera vez por Action Comics, perteneciente al grupo de cómics estadounidenses publicados por DC Comics. El personaje fue creado por el escritor estadounidense Jerry Siegel y el artista canadiense Joe Shuster en 1933 cuando ambos se encontraban viviendo en Cleveland, Ohio.",
    img: "https://preview.redd.it/pasen-edits-de-personajes-mariwanos-como-este-v0-1ao2brfr8uka1.png?width=1092&format=png&auto=webp&s=7ea81d6daefea27725893ade9477191693dcb526",
    link: "https://es.wikipedia.org/wiki/Superman",
        compañia: "dc"
  },
  {
    nombre: "weedsh",
    descripcion: "Flash (conocido también como The Flash y traducido en español: Destello) es el nombre de varios superhéroes ficticios que aparecen en los cómics estadounidenses publicados por DC Comics. Creado por el escritor Gardner Fox y el artista Harry Lampert",
    img: "https://preview.redd.it/06udpm69u2t01.jpg?width=640&crop=smart&auto=webp&s=8b8f090032d0833c4b09e927a806c911b16b2442",
    link: "https://es.wikipedia.org/wiki/Flash_(DC_Comics)",
        compañia: "dc"
  }
  ,
  {
    nombre: "Robin",
    descripcion: "Robin es el alias de varios superhéroes ficticios que aparecen en los cómics estadounidenses publicados por DC Comics. El personaje fue creado originalmente por Bob Kane, Bill Finger y Jerry Robinson, para servir como contraparte menor del superhéroe Batman. La primera encarnación del personaje, Dick Grayson",
    img: "https://www.mundodeportivo.com/alfabeta/hero/2024/05/robin-batman-dc-comics.jpg?width=1200&aspect_ratio=16:9",
    link: "https://es.wikipedia.org/wiki/Robin_(DC_Comics)",
        compañia: "dc"
  }
  ,
  {
    nombre: "Wanda Maximoff",
    descripcion: "Wanda Maximoff es una superheroína ficticia que aparece en los cómics publicados por Marvel Comics. Apareció por primera vez en X-Men #4 y fue creada por Stan Lee y Jack Kirby, debutando en la denominada Edad de Plata de los Cómics",
    img: "https://upload.wikimedia.org/wikipedia/en/d/d9/Elizabeth_Olsen_as_Wanda_Maximoff.jpg",
    link: "https://es.wikipedia.org/wiki/Bruja_Escarlata",
        compañia: "marvel"
  }
  ,
  {
    nombre: "Smoki",
    descripcion: "Flash (conocido también como The Flash y traducido en español: Destello) es el nombre de varios superhéroes ficticios que aparecen en los cómics estadounidenses publicados por DC Comics. Creado por el escritor Gardner Fox y el artista Harry Lampert",
    img: "https://preview.redd.it/pasen-edits-de-personajes-mariwanos-como-este-v0-sxpgqb421uka1.jpeg?width=534&format=pjpg&auto=webp&s=9b81004e63b459245b272c159745e5a7bb7adc88",
    link: "https://es.wikipedia.org/wiki/Loki_(Marvel_Comics)",
        compañia: "marvel"
    
  }
  ,
  {
    nombre: "Doctor entreñido",
    descripcion: "El Doctor Stephen Strange (Doctor Extraño en España, donde se le cambia el nombre a Stephen Extraño) es un personaje ficticio que aparece en cómics estadounidenses publicados por Marvel Comics. Creado por el artista Steve Ditko y el escritor Stan Lee",
    img: "https://preview.redd.it/gort-cant-lose-vote-against-dr-strain-v0-cfbbvk3n0uoa1.jpg?width=533&format=pjpg&auto=webp&s=652444b633f6ee519dbc7c197d49285c342175b1",
    link: "https://es.wikipedia.org/wiki/Doctor_Strange",
    compañia: "marvel"
  }
]);


const searchQuery = ref('');


const expandedIndex = ref(null);


const filteredSuperheroes = computed(() => {
  return superheroes.value.filter((superheroe) =>
    superheroe.nombre.toLowerCase().includes(searchQuery.value.toLowerCase())
  );
});


function toggle(index) {
  expandedIndex.value = expandedIndex.value === index ? null : index;
}
</script>

<template>
  <div>
  
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-navbar-brand href="#">Menu</b-navbar-brand>
      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav class="ml-auto">
          <b-nav-form>
            <b-form-input
              v-model="searchQuery"
              size="sm"
              class="mr-sm-2"
              placeholder="Buscar"
            ></b-form-input>
            <b-button size="sm" class="my-2 my-sm-0" type="submit">Buscar</b-button>
          </b-nav-form>
          <form>
              <input type="checkbox" id="compañia">
              <label>Marvel</label>
            </form>
            <form>
              <input type="checkbox" id="compañia">
              <label>DC</label>
            </form>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <b-container class="mt-4">
      <b-row>
        <b-col
          v-for="(superheroe, index) in filteredSuperheroes"
          :key="index"
          cols="12"
          md="6"
          lg="4"
          class="mb-4"
        >
          <b-card :title="superheroe.nombre" tag="article" class="mb-2">
            <img
              :src="superheroe.img"
              :alt="superheroe.nombre"
              class="card-img-top"
              style="height: 400px; object-fit: cover;"
            />
            <b-button @click="toggle(index)" variant="link" class="p-0 text-primary">
              {{ expandedIndex === index ? 'Leer menos' : 'Leer más' }}
            </b-button>
            <div v-if="expandedIndex === index">
              <b-card-text>{{ superheroe.descripcion }}</b-card-text>
            </div>
            <br />
            <b-button :href="superheroe.link" variant="primary" class="mt-2">Ver Más Información</b-button>
          </b-card>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template> 
