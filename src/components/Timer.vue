<template>
    <div class="timer">
        <div :class="{'timer__time': true, 'active': timerState == 'running' }">
            <span>{{ formattedTime }}</span>
        </div>
        <div :class="{'timer__line':true, 'active_bg': timerState == 'running'}"> </div>
        <div :class="{'timer__icon':true, 'active': timerState == 'running' }">
            <i 
            v-if="timerState !== 'running'"
            class="fa fa-play play icon-margin" 
            aria-hidden="true"
            @click="start"
            >
            </i>
            <i 
            v-else
            class="fa fa-pause pause icon-margin " 
            aria-hidden="true"
            @click="pause"
            >
            </i> 
            <i
             class="fa fa-stop icon-margin" 
             aria-hidden="true"
             @click="stop"
             >
             </i>  
        </div>
    </div>
</template>

<script>
export default {
    name: "Timer",
    data() {
        return {
            timerState: 'stopped',
            currentTimer: 0,
            ticker: undefined,
        }
    },
    computed: {
        formattedTime() {
            if (this.currentTimer < 60) {
                return new Date(this.currentTimer * 1000).toISOString().substr(17, 2);
            } 
            if (this.currentTimer >= 60 ) {
                return new Date(this.currentTimer * 1000).toISOString().substr(14, 5)
            }
            if (this.currentTimer >= 3600) {
                return new Date(this.currentTimer * 1000).toISOString().substr(11, 8);
            }
        }
    },
    // filters: {
    //     formattedTimeHours(value) {
    //         return new Date(value * 1000).toISOString().substr(11, 2);
    //     },
    //     formattedTimeMinutes(value) {
    //         return  new Date(value * 1000).toISOString().substr(14, 2);   
    //     },
    //     formattedTimeSeconds(value) {
    //         return new Date(value * 1000).toISOString().substr(17, 2);
    //     }
    // },
    methods: {
        start() {
            if (this.timerState !== 'running') {
                this.tick();
                this.timerState = 'running';
            }
        },
        stop() {
            clearInterval(this.ticker)
            this.currentTimer = 0;
            this.timerState = "stopped";
        },
        pause() {
            clearInterval(this.ticker);
            this.timerState = 'paused';
        },
        tick() {
            this.ticker = setInterval(() => {
                this.currentTimer++;
            }, 100)
        },
    }
}
</script>

<style >
.timer {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 225px;
    height: 120px;
    margin: 22px 25px;
    background: #696969;
}
.timer__time {
    font-family: 'Gotham Pro Light';
    font-size: 22px;
    font-style: normal;
    font-weight: 400;
    text-align: center; 
    padding: 16px;
    color: #9E9E9E;
}
.timer__line {
    width: 100%;
    height: 2px;
    background-color:  #9E9E9E;
}
.timer__icon {
    display: flex;
    padding: 20px 75px;
    color: #9E9E9E;
    font-size: 20px;
}
.icon-margin {
    margin: 0px 24px;
    cursor: pointer;
}
.active {
    color: white;
}
.active_bg {
    background-color: white;
}
</style>