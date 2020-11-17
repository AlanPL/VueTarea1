<template>
  <div class="hello">    
    <h1>Tarea 1</h1>
    <h2>Lista ordenada de palabras separadas por comas</h2>    
    <input type="text" placeholder="Escribir lista" v-model="cadenaInput" >        
    <div class="lista" v-if="items.length>0">
      <ol id="example-1" >
        <li v-for="item in items" :key="item.id">
          {{ item.name }} : {{ item.quantity }}
        </li>        
      </ol>
    </div>    
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String    
  },  
  data() {       
    return {      
      cadena: "",
      items: [],
    }; 
    
  },
  computed: {
    cadenaInput: {
      get(){
        return this.cadena;
      },
      set(newValue){
        this.cadena = newValue;
        this.organizar();
      }
    }
  },
  methods:{
    organizar: function(){      
      var auxArr = this.cadena.split(",");      
      this.items = [];

      //para cada string separado por comas
      auxArr.forEach(element => {        
        //quita espacios extras y luego lo divide
        var info = element.trim().split(" ");
                
        // si el ultimo elemento aun no se escribe, no se renderiza
        if(info.length<2){
          return;
        }
        var obj = {
          name: info[0],
          quantity: info[1]
        };
        this.items.push(obj);
      });
              
    }           
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input[type=text] {
  width: 80%;
  padding: 12px 20px;
  margin: 8px 0;
  box-sizing: border-box;
  border: none;
  background-color: #41B883;
  color: white;
  font-size: 20px;
  border-radius: 4px;
}

input[type=text]:focus {  
  border: none;
  border: 2px #555;
}

.lista{    
  background-color: #2d312f;
  color: white;
  font-size: 20px;
  border-radius: 4px;        
  width: 80%;
  margin: auto;
  padding-top: 10px;
  padding-bottom: 10px;    
  text-align: left;
}

</style>
