<template>
    <div class="main-wrapper">
        <Timer/>
        <Timer v-for="timer in timersArray" :key="timer.id"/>
        <AddTimer @add-new-timer="$emit('add-new-timer')"/>
    </div>
</template>


<script>
import Timer from './Timer'
import AddTimer from './AddTimer'

export default {
    name: 'MainWrapper',
    components: {
        Timer, 
        AddTimer
    },
    props: ['timersArray']
}
</script>

<style>
.main-wrapper {
    max-width: 825px;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    margin: 0 auto;
}
@media (min-width: 768px) and (max-width: 1023px) {
    .main-wrapper {
        max-width: 566px;
    }
}
@media (min-width: 320px) and (max-width: 767px) {
    .main-wrapper {
        flex-direction: column;
    }
}
</style>