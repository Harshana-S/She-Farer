<template>
    <div>
        <VuetoComplete 
            v-model="query"
            :auto-complete-list="list"
            :styles="styles">
        </VuetoComplete>
   </div>
</template>
<script>
import VuetoComplete from 'vueto-complete';
import { type } from 'os';

const styles = {
    container: {
      maxWidth: '500px',
    },
    input: {
      border: '1px solid gray',
    },
    focusedInput: {
      background: '#e0e0e0',
    },
    resultsList:{
        
    }
  };

export default {
    data:function(){
        return{
            query:'',
            styles,
            list:[
                'Bangalore','Chennai','Kolkata','Pune','Mumbai','Delhi'
            ],
            components:{
                VuetoComplete
            }
        }
    }
}
</script>

