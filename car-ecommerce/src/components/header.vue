<template>
    <div class="d-flex">
        <div class="mx-2">
            <select class="form-select" aria-label="Default select example">
                <option selected>Category</option>
                <option value="1">Telsa</option>
                <option value="2">Porsche</option>
                <option value="3">Toyota</option>
                <option value="4">Honda</option>
                <option value="5">Mazda</option>
                <option value="6">Mercedes-Benz</option>
                <option value="7">Lexus</option>
                <option value="8">Lamborghini</option>
                <option value="9">Audi</option>
                <option value="10">BMW</option>
            </select>
        </div>
        

        <div>
            <select class="form-select" aria-label="Default select example">
                <option selected>Sort by:</option>
                <option value="1">Price: Low to High</option>
                <option value="2">Price: High to Low</option>
                <option value="3">Newest Arrivals</option>
            </select>
        </div>
    </div>
</template>

<script>

export default ({
    nama: 'Header',
    data() {
        
    },
    props: {
        
    }

})
</script>
