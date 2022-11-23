<template>
    <div> <!-- 원룸들 리스트를 Item이라는 변수로 두고 리스트의 갯수를 i로 둔다 -->
    <img :src="원룸들.image" class="room-img">
    <h4 @click="$emit('openModal', 원룸들.id)">{{원룸들.title}}</h4>
    <p>{{원룸들.content}}</p>
    <p>{{원룸들.price}} 원</p>
</div>
</template>

<script>
export default {
    name : 'CardPage',
    props : {
        원룸들 : Object,
    }
}
</script>

<style>

</style>