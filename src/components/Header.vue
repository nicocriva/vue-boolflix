<template>
  <header class="w-100">
    
    <h3 class="title ms-3 float-start">Boolflix</h3>
    <form action="" class="float-end me-3">
        <input type="text" class="mx-2" placeholder="Inserisci titolo film">
        <button class="px-1">Search</button>
    </form>

  </header>
</template>

<script>
export default {
    name: 'Header',
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

    .title{
        color: red;
    
    }

    form *{
        border-radius: 10px;
        padding-left: 10px;
    }

   
}
</style>
