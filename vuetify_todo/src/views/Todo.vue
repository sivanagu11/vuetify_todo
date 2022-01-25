<template>
  <v-container mt-16>
    <div class="radius">
      <v-row justify="center" class="my-12">
        <v-card class="pt-10 px-16" height="500px" width="400px" overflow="hidden" display="fixed" > 
      <div class="mt-n5" >
       
        <h2>Today</h2>
        <v-checkbox 
        v-model="checkbox"
        label="learn vuejs"
        >
        </v-checkbox>
          <v-checkbox 
        v-model="checkbox"
        label="practice vuejs"
        >
        </v-checkbox>
          <v-checkbox 
        v-model="checkbox"
        label="go to office"
        >
        </v-checkbox>
        
         <h2>Tommorrow</h2>
        <v-checkbox 
        v-model="checkbox"
        label="learning github"
        >
        </v-checkbox>
          <v-checkbox 
        v-model="checkbox"
        label="push code into the gitgub"
        >
        </v-checkbox>
        <v-checkbox 
        v-model="checkbox"
        label="cloning the project"
        >
        </v-checkbox>
      
         

      </div>
        </v-card>
      </v-row>
    </div>
  </v-container>
</template>

<script>
export default{
data (){
  return{
    checkbox:true
  }

},

}
  
</script>





