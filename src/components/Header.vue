<template>
  <header class="w-100">
    
    <h3 class="title ms-3 float-start text-danger">Boolflix</h3>
    <form action="" class="float-end me-3">
        <input type="text" class="mx-2" 
            @keyup="$emit('search', inputText)"
            placeholder="Inserisci titolo film"
            v-model="inputText"
            />
        <button class="px-1" @click.prevent="$emit('search', inputText)">Search</button>
    </form>

  </header>
</template>

<script>
export default {
    name: 'Header',
    data(){
        return {
            inputText: ''
        };
    }
}
</script>

<style scoped lang="scss">
header{
    background-color: black;
    height: 50px;

    .title, form{
        position: relative;
        top: 50%;
        transform: translate(0, -50%);
    }

    form{
        input, button{
            border-radius: 10px;
            padding-left: 10px;
        }
    }

   
}
</style>
