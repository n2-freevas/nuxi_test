<script lang="ts">
    export default {
        props: {
            width: {
                type: String,
                required: false,
                default: "unset"
            },
            pushCallBack: {
                type:Function,
                require: true,
            }
        },
        data(){
            return{
                isButtonShrink: false,
                isButtonBurst: false
            }
        },
        computed: {
            styleSetting(){
                return {
                    '--vcButtonWidth': this.width
                }
            }
        },
        methods:{
            mouseDownEvent(){
                this.isButtonShrink = true
                this.isButtonBurst = false
            },
            mouseUpEvent(){
                this.isButtonShrink = false
                this.isButtonBurst = true
                this.pushCallBack!()
            }
        },
    }
</script>

<template>
    <div 
        class="vcButton"
        :class="{ 
            shrink: isButtonShrink,
            burst: isButtonBurst
        }"
        :style="styleSetting"
        @contextmenu.prevent
        @mousedown="mouseDownEvent"
        @touchstart="mouseDownEvent"
        @touchend="mouseUpEvent"
        @mouseup="mouseUpEvent"
    >
        <div
            class="vcButtonBG"
            :class="{ 
                burst: isButtonBurst
            }"
        >
        </div>
        <slot/>
    </div>
</template>

<style lang="scss" scoped>
    .vcButton{
        width: var(--vcButtonWidth);
        position: relative;
        margin: 0 auto;
        border: solid 1px #c4c4c4;
        box-shadow: #929292 2px 2px 3px;
        padding:15px 50px;
        font-family: $font;
        font-weight: 600;
        color:#525252;
        text-align: center;
        transform-origin: center;
        font-size: 20px;
        border-radius: 10px;
        transition: 0.3s;
        user-select: none;
        background: white;
        .vcButtonBG{
            position: absolute;
            width:102%;
            height:102%;
            transform-origin: center;
            top:0;
            left:0;
            border: solid 3px $primary;
            border-radius: 10px;
            opacity: 0;
            &.burst{
                animation: burstAnimBG 0.4s ease-out;
            }
            @keyframes burstAnimBG {
                0%{
                    opacity: 0;
                }
                10%{
                    opacity: 1;
                }
                60%{
                    scale:1.3;
                }
                100%{
                    scale:0.5;
                }
            }
        }
        &.shrink{
            animation: shrinkAnim 0.2s ease-out forwards;
        }
        &.burst{
            animation: burstAnim 1s ease-out;
        }
        @keyframes shrinkAnim {
            0%{
                scale: 1;
            }
            100%{
                scale: 0.8;
                border: solid 1px $primary;
                box-shadow: $primary 2px 2px 3px;
            }
        }
        @keyframes burstAnim{
            0%{
                scale:0.8;
                border: solid 1px $primary;
                box-shadow: $primary 2px 2px 3px;
            }
            10% {
                scale:1.1;
            }
            30% {
                scale: 1;
                border: solid 1px $primary;
                box-shadow: $primary 2px 2px 3px;
            }
            100%{
                border: solid 1px #c4c4c4;
                box-shadow: #929292 2px 2px 3px;
            }
        }
    }
</style>
