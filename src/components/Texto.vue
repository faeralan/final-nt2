<template>

  <section class="src-components-texto">
    <div>
      <label for="text">Color</label>
      <input 
        type="text"
        id="text"
        class="form-control"
        v-model="color"
      >

      <label for="text">Fondo</label>
      <input 
        type="text"
        id="text"
        class="form-control"
        v-model="fondo"
      >

      <label for="text">Size</label>
      <input 
        type="text"
        id="text"
        class="form-control"
        v-model="size"
      >  
    </div>
    <div>
      <label for="text">Texto</label>
        <input 
          type="text"
          id="text"
          class="form-control"
          v-model="texto"
          :style="{
            color: color,
            'background-color': fondo,
            'font-size': size
          }"
        >
      <p v-if="calcularTotPalabras >= 1">Cantidad total de palabras {{calcularTotPalabras}}</p>
      <p v-else-if="calcularTotPalabras == 0">No hay nada escrito</p>
    </div>

    <div>
      <table border=1>
        <thead>
          <tr>
            <th>Número de pregunta</th>
            <th>Respuesta</th>
          </tr>
        </thead>

        <tbody v-if="preguntas.length > 0">
          <tr v-for="(dato, i) in preguntas" :key="i">
            <td>{{dato.pregunta}}</td>
            <td>{{dato.respuestas.join()}}</td>
          </tr>
          
        </tbody>

      </table>
    </div>
  </section>

</template>

<script>

  export default  {
    name: 'src-components-texto',
    props: [],
    mounted () {

    },
    data () {
      return {
        texto: "",
        color: "black",
        fondo: "white",
        size: "12px",
        preguntas: [
          {pregunta: 1, respuestas: ['b']},
          {pregunta: 2, respuestas: ['c']},
          {pregunta: 3, respuestas: ['a','b']},
          {pregunta: 4, respuestas: ['c','d']},
          {pregunta: 5, respuestas: ['a','d']}
        ]
      }
    },
    methods: {

    },
    computed: {
      calcularTotPalabras() {
      let text = this.texto.trim();
      let total=0;
      if(text != ''){
        let espacios = /[ ]+/g
        text = text.replace(espacios, " ")
        let aux = text.split(" ");
        
        total = aux.length;
      }

      return total
    },
    }
}


</script>

<style scoped lang="css">
  .src-components-texto {

  }
</style>
