<template>
    <vue-autosuggest
        :suggestions="[{data:['Bangalore','Chennai','Kolkata','Pune','Mumbai','Delhi']}]"
        :input-props="{id:'autosuggest_input',onInputChange: this.onInpuChange, placeholder:'Enter your search destination'}"
        :onSelected="clickHandler"
        >
    <div slot-scope="{suggestion}">
        <ul>
        <li class="suggestion-item">{{suggestion.item}}</li>
        </ul>  
    </div>
    </vue-autosuggest>
</template>
<script>
import { VueAutosuggest } from 'vue-autosuggest';
export default {
    components:{
        VueAutosuggest
    },
      
}
</script>
<style scoped>
input{
    width:inherit;
}
li{
    list-style-type: lower-alpha;
}
</style>
