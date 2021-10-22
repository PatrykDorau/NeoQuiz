<template>
<div>
{{name}}
{{picture}}
</div>
</template>

<script>
export default {
    name:'productForm',
    props: {
        name: String,
        picture: Number
    }
}
</script>

<style>

</style>