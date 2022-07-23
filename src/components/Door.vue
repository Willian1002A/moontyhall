<template>
    <div class="door-area">
        <div class="door-frame" :class="{ selected: selected && !open }">
            <Gift v-if="open && hasGift"/>
        </div>
        <div class="door" 
            @click="selected = !selected"
            :class="{ open }">
            <div class="number" :class="{ selected }">
                {{ number }}
            </div>
            <div class="knob" 
                :class="{ selected }"
                @click.stop="open = true"
                ></div>
        </div>
    </div>
</template>

<script>
import Gift from './Gift.vue';
export default {
    name: "Door",
    components: { Gift },
    props: {
        number: {},
        hasGift: { type: Boolean }
    },
    data: function(){
        return {
            open: false,
            selected: false
        }
    }
}
</script>

<style>
    :root{
        --door-border: 5px solid brown;
        --selected-border: 5px solid yellow;
    }
    .door-area {
        position: relative;
        width: 200px;
        height: 310px;
        border-bottom: 10px solid #AAA;
        margin-bottom: 20px;
        font-size: 3rem;
        justify-content: center;
        display: flex;
    }
    .door-frame{
        position: absolute;
        height: 300px;
        width: 180px;

        border-left: var(--door-border);
        border-top: var(--door-border);
        border-right: var(--door-border);

        display: flex;
        justify-content: center;
        align-items: flex-end;
    }
    .door {
        position: absolute;
        top:  5px;
        height: 295px;
        width: 170px;
        background-color: chocolate;

        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 20px;
    }
    .door .knob {
        height: 20px;
        width: 20px;
        border-radius: 10px;
        background-color: brown;
        align-self: flex-start;
        margin-top: 60px;
    }
    .door-frame.selected {
        border-left: var(--selected-border);
        border-top:  var(--selected-border);
        border-right: var(--selected-border);
    }
    .door > .number.selected {
        color: yellow;
    }
    .door > .knob.selected {
        background-color: yellow;
    }
    .door.open{
        background-color: #0007;
    }
    .door.open .knob{
        display: none;
    }
    .door.open .number {
        display: none;
    }
    *{
        --base-resolution: 1920;
        --actual-resolution: 360
    }
    @media (min-width: 400px) {
        *{
            --actual-resolution: 400;
        }
    }
    @media (min-width: 640px) {
        *{
            --actual-resolution: 640;
        }
    }
    @media (min-width: 1024px) {
        *{
            --actual-resolution: 1024;
        }
    }
    @media (min-width: 1360px) {
        *{
            --actual-resolution: 1360;
        }
    }
    @media (min-width: 1920px) {
        *{
            --actual-resolution: 1920;
        }
    }
        *{
        --mult-factor: calc(var(--actual-resolution)/var(--base-resolution) * 1.5);
    }
    @media (orientation: portrait) {
        *{
            --mult-factor: calc(var(--actual-resolution)/var(--base-resolution) * 2.5);
        }
    }
    *{
        --door-border-size: calc(5px * var(--mult-factor));
        --door-area-width: calc(200px * var(--mult-factor));
        --door-area-height: calc(310px * var(--mult-factor));
        --door-area-border-bottom-size: calc(10px * var(--mult-factor));
        --door-area-margin-bottom: calc(20px * var(--mult-factor));
        --door-area-font-size: calc(3rem * var(--mult-factor));
        --door-frame-width: calc(300px * var(--mult-factor));
        --door-frame-height: calc(180px * var(--mult-factor));
        --door-top: calc(5px * var(--mult-factor));
        --door-width: calc(170px * var(--mult-factor));
        --door-height: calc(295px * var(--mult-factor));
        --door-padding: calc(20px * var(--mult-factor));
        --door-knob-width-height: calc(20px * var(--mult-factor));
        --door-knob-border-radius: calc(10px * var(--mult-factor));
        --door-knob-margin-top: calc(60px * var(--mult-factor));
    }

    :root{
        --door-border: var(--door-border-size) solid brown;
        --selected-border: var(--door-border-size) solid yellow;
    }
    .door-area {
        width: var(--door-area-width);
        height: var(--door-area-height);
        border-bottom: var(--door-area-border-bottom-size) solid #AAA;
        margin-bottom: var(--door-area-border-margin-bottom);
        font-size: var(--door-area-font-size);
    }
    .door-frame{
        height: var(--door-frame-width);
        width: var(--door-frame-height);
        border-left: var(--door-border);
        border-top: var(--door-border);
        border-right: var(--door-border);
    }
    .door {
        top:  var(--door-top);
        width: var(--door-width);
        height: var(--door-height);
        padding: var(--door-padding);
    }
    .door .knob {
        width: var(--door-knob-width-height);
        height: var(--door-knob-width-height);
        border-radius: var(--door-knob-border-radius);
        margin-top: var(--door-knob-margin-top);
    }
    .door-frame.selected {
        border-left: var(--selected-border);
        border-top:  var(--selected-border);
        border-right: var(--selected-border);
    }

</style>