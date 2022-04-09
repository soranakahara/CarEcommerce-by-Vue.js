<template>
    <div>
        <div class="card m-2" style="width: 18rem;">
            <div class="card-body">
                <img v-bind:src="carItem.img" class="card-img-top" alt="...">
                <h5 class="card-title pt-2">{{ carItem.title }}</h5>
                <p class="card-text">Category: {{ carItem.category }}</p>
                <p class="card-text">Price: ${{ carItem.price }}</p>
                <p class="card-text">Date: {{ carItem.date }}</p>  
            </div>
        </div>
    </div>
</template>

<script>

export default {
  name: 'ItemCard',
  // 親からv-bindでオブジェクトを受け取る
  props: ["carItem"],
}
</script>
