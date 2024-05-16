<script setup>
import { ref, computed } from "vue";

const items = {"1":"Tema 1","2":"Tema 2","3":"Tema 3","4":"Tema 4"};

const checked = ref(false);

const counter ={"1":ref(0),"2":ref(0),"3":ref(0),"4":ref(0)}
const checked1 ={"1":ref(false),"2":ref(false),"3":ref(false),"4":ref(false)}
const list ={"1":"+","2":"+","3":"+","4":"+"}


// const message = computed (()=>{
//     let uno;
//     if(checked.value){
//         uno = true;
//     }else{
//         uno = false;
//     }
//     return uno;
// })

function message1(item){
    let dos;
    if(checked1[item]){
        dos=false;
        list[item]="+"
    }else{
        dos=true;
        list[item]="-"
    }
    return dos;
}

function estado(item){
    if(checked.value){
        counter[1]=0;
        counter[2]=0;
        counter[3]=0;
        counter[4]=0;
        counter[item]=1;
    }else{
        counter[1]=1;
        counter[2]=1;
        counter[3]=1;
        counter[4]=1;
        counter[item]=0;
    }
}
function validar(item){
    checked1[1]=false;
    checked1[2]=false;
    checked1[3]=false;
    checked1[4]=false;
    checked1[item]=!checked1[item];
    checked = message1(item);
}

</script>
<template>
    <div class="w-1/2 h-1/2 text-blue-900 flex flex-col" v-for="(item, index) in items">
        
        <button class="bg-blue-300 flex rounded-lg justify-evenly m-3 p-5 w-full text-left" @click="validar(item), estado(item)">    
            {{ items[index] }} 
            <div>
                {{ list[index]}}
            </div>
            
        </button>
        <div v-show="counter[item] > 0"  class="bg-blue-200 h-44 rounded-lg justify-evenly m-3 p-5 w-full text-left">
            {{ "texto del tema " + items[index] }}
        </div>

    </div>
    
</template>