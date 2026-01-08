<template>
  <div class="opciones-container">
    <ul>
        <li>Pokemon1</li>
        <li>Pokemon2</li>
        <li>Pokemon3</li>
        <li>Pokemon4</li>
    </ul>
  </div>
</template>

<script>
export default {
    

}
</script>

<style>
    ul{
        list-style-type: none;
        
    }
    li{
        background-color: white;
        border-radius: 5px;
        border: 1px solid;
        cursor: pointer;
        width: 250px;
        margin-top: 10px;
    }
    .opciones-container{
        display: flex;
        justify-content: center;
    }

</style>