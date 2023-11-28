<template>
    <div class="col-lg-12 mb-4">
        <div class="main-button-red">
            <h2>Page viewer template</h2>
            <h3>{{ pages[activePages].content }}</h3>
        </div>
    </div>
</template>

<script>
export default {
    props: ['pages', 'activePages'],
}
</script>