<template>
    <div class="hello">
        {{msg}}
    </div>
</template>

<script>
export default {
    name: 'hello',
    data() {
        return {
            msg: 'Vue.js 앱에 오신 걸 환영합니다.'
        }
    }
}
</script>

<!-- CSS 범위 지정을 위해 해당 컴포넌트에만 "scoped 속성을 추가하세요. -->
<style scoped>
</style>