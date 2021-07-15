<template>
  <header class="w-100 position-fixed d-flex justify-content-between align-items-center">
    
    <div class="d-flex align-items-center">
        <h3 class="title ms-3 mb-0 text-danger">Boolflix</h3>
        <ul>
            <li>Home</li>
            <li>Serie TV</li>
            <li>Film</li>
            <li>Originali</li>
            <li>Aggiunti di recente</li>
            <li>La mia lista</li>
        </ul>
    </div>
    <form action="" class="me-3">
        <input type="text" class="mx-2" 
            @keyup.enter="$emit('search', inputText)"
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
    background-color: rgba(0, 0, 0, 1);
    height: 50px;
    z-index: 500;

    .title{
        cursor: pointer;
    }

    ul{
        list-style: none;
        margin-bottom: 0;

        li{
            font-size: 14px;
            float: left;
            margin: 0 10px;
            color: rgba(255, 255, 255, 0.7);
            cursor: pointer;

            &:hover{
                color: white;
            }
        }

    }

    form{
        input, button{
            border-radius: 10px;
            padding-left: 10px;
        }
    }

   
}
</style>
