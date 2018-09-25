<template>
    <div class="stopwatch">
        <h2 class="stopwatch-heading">Stopwatch</h2>
        <p>{{hours}}:{{minutes}}:{{seconds}}</p>
        <button @click="start()">Start</button>
        <button @click="stop()">Stop</button>
        <button @click="reset()">Reset</button>
    </div>
</template>

<script>
    export default {
        data: function () {
            return {
                hours:0,
                minutes:0,
                seconds:0,
                isActive:false
            }
        },
        methods: {
            start() {
                this.isActive = true;
                setInterval(() => {
                    if(this.isActive) {
                        this.seconds++;
                        if (this.seconds % 60 === 0) {
                            this.minutes++;
                            if (this.minutes === 60) {
                                this.hours++;
                                this.minutes = 0;
                            }
                            if (this.seconds === 60) {
                                this.seconds = 0;
                            }
                        }
                    }
                }, 1000)
            },
            stop() {
                this.isActive = false;
            },
            reset() {
                this.isActive = false;
                this.seconds = 0;
                this.minutes = 0;
                this.hours = 0;
            }
        }
    }
</script>

<style>
    .stopwatch{
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }
    button{
        width: 60px;
        margin: 10px;
    }
</style>
