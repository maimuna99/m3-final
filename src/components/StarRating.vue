<script setup>
import { ref } from 'vue';

const rate = toRef(props, 'rate');
</script>

<template>
<div id="rating-info">{{rate}}</div>
<div>
        <b>Rating: </b>{{response.rating}}/5
        <span v-if="response.rating >= 4.5">⭐ ⭐ ⭐ ⭐ ⭐</span>
        <span v-else-if="response.rating >= 3.5">⭐ ⭐ ⭐ ⭐</span>
        <span v-else-if="response.rating >= 2.5">⭐ ⭐ ⭐</span>
        <span v-else-if="response.rating >= 1.5">⭐ ⭐</span>
        <span v-else>⭐</span><br/>
      </div>


</template>

<style>
.div{
    background-color:whitesmoke;
    height: 50px;
    text-align:right;
}
</style>