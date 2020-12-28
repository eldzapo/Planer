<template>

   <div id="todo-container">

        <div id="Todo-import">

                <div class="Image-wrapper">
                      <b-img src="https://picsum.photos/1024/400/?image=41" fluid alt="Responsive image"></b-img>
                </div>

                          <h1>Todo List</h1>
                               <p>Vnesi svoje plane za danes! </p>


               <div class="import-sekcija">

                    <div v-if="!ureja">
                      
                          <b-form-input type="text" v-model="naredi" class="forma" placeholder="Vnesi svoj današnji Todo!"></b-form-input>
                          <b-button type="submit" value="add" @click="saveNaredi" onsubmit="checkForm" id="shrani" variant="primary" >Shrani!</b-button>


                      </div>


                      <div v-else>

                            <b-form-input type="text" v-model="naredi"></b-form-input>
                            <b-button type="submit" value="popravi" @click="popraviNaredi" onsubmit="checkForm" id="popravi" variant="danger">Popravi</b-button>

                              

                      </div>

                </div>

        </div>
                  <div class="plani"> Moji plani : </div>
                        <ol>
                         
                            <li v-for="(naredi, index)  in lista" :key="naredi">
                                {{ naredi }}

                              <div id="btnWrapper">
                                  <b-icon @click="urediNaredi(index,naredi)" class="brush" icon="brush " font-scale="1.2"></b-icon>
                                  <b-icon @click="izbrisiNaredi(index)" class="trash" icon="trash" font-scale="1.2" color="red">Izbrisi</b-icon>
                              </div>
                            </li>
                        </ol> 


   </div>

</template>


<script>
 export default {

            name:"Todo",
            data(){ 
                return {
                    ureja:false,
                    izbraniIndex: "",
                    naredi: "",
                    disabled:true,
                    lista: [
                          ]
                  } 
                    },

            methods : 
            
                  { 
                        saveNaredi(){
                          if (this.naredi > "") 
                          this.lista.push(this.naredi);
                          this.naredi = ""
                                
                          },
                          urediNaredi(index,naredi){
                            this.naredi = naredi
                            this.izbraniIndex = index
                            this.ureja = true     
                          },
                          popraviNaredi() { 
                            this.lista.splice(this.izbraniIndex,1,this.naredi)
                            this.ureja = false
                            this.naredi="";
                            document.getElementById ( "Trash ").disabled = true 
                          },
                          izbrisiNaredi() { 
                            this.lista.splice(this.izbraniIndex,1)
                          },
                          
                      }
                        
                  

                  }  
                
              
              
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>






#todo-container h1 {
    color:teal;
}

p { 
    margin-top:20px;
    margin-bottom:30px;
    font-size:15px;
    color:#CCC;
}


.forma { 

  display:inline-block;
 
}


.gumb { 
  display:inline-block;
  position: relative;
  justify-content: unset;
  margin:5px;
}


ol {
  display:block;
  margin-top:40px;
}


li { 

  justify-content:left;
  display:flex;
  margin-top:20px;
  border-radius:20px;
  padding:20px;
  margin-right:40px;
  background-color:white;
  min-width: auto;
  word-wrap: break-word;
  -webkit-box-shadow: 5px 4px 11px 7px #CDCDCD; 
  box-shadow: 5px 4px 11px 7px #CDCDCD;  
}


#btnWrapper {   
   display: inline-block;
   position:relative;
   right:0px auto;
}


li #btnWrapper .b-icon {    
   margin-left:10px;

}


.b-icon:hover {
  transform: scale(1.20);
  transition:0.5s ease;
}



.plani{ 

  margin-top:30px;
  text-align: center;
  font-size:23px;
  color:#ccc;
}


#shrani { 

  margin-top:30px;
  border-radius:10px;
  
 
}

#popravi { 

  border-radius:30px;
  margin-top:10px;
}

#todo-container { 
    background-color:#fff;
    min-height: 350px;
    margin-top:50px;
    padding:30px;
    border-radius:20px;
    -webkit-box-shadow: 5px 4px 11px 7px #CDCDCD; 
    box-shadow: 5px 4px 11px 7px #CDCDCD;
}

#todo-container h1 { 
  margin-top:40px;
}

.import-sekcija { 
  margin-top:20px;
  margin-left:40px;
  margin-right:40px;
}

.import-sekcija .button { 
  margin:20px;
}


</style>
