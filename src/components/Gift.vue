<template>
    <div class="gift">
        <div class="gift-tie-1"></div>
        <div class="gift-tie-2"></div>
        <div class="gift-top"></div>
        <div class="gift-body"></div>
    </div>
</template>

<script>
export default {
    name: "Gift"
}
</script>

<style>
    .gift {
        position: relative;
        display: flex;
        flex-direction: column;
        align-items: center;
        z-index: 10;
    }
    .gift-top{
        /* width: 100px;
        height: 25px; */
        background-color: #7aa944;
    }
    .gift-body {
        /* width: 90px;
        height: 60px; */
        background-color: #5c7e32;
    }
    .gift-tie-1 {
        position: absolute;
        /* width: 15px;
        height: 85px; */
        background-color: red;
    }
    .gift-tie-2 {
        position: absolute;
        /* top: 40px;
        width: 90px;
        height: 15px; */
        background-color: red;
    }
    *{
        --base-resolution: 1920;
        --actual-resolution: 360;
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
        --gift-top-width: calc(100px * var(--mult-factor));
        --gift-top-height: calc(25px * var(--mult-factor));
        --gift-body-width: calc(90px * var(--mult-factor));
        --gift-body-height: calc(60px * var(--mult-factor));
        --gift-tie-1-width: calc(15px * var(--mult-factor));
        --gift-tie-1-height: calc(85px * var(--mult-factor));
        --gift-tie-2-top: calc(40px * var(--mult-factor));
        --gift-tie-2-width: calc(90px * var(--mult-factor));
        --gift-tie-2-height: calc(15px * var(--mult-factor));
    }
    .gift-top{
        width: var(--gift-top-width);
        height: var(--gift-top-height);
    }
    .gift-body {
        width: var(--gift-body-width);
        height: var(--gift-body-height);
    }
    .gift-tie-1 {
        width: var(--gift-tie-1-width);
        height: var(--gift-tie-1-height);
    }
    .gift-tie-2 {
        top: var(--gift-tie-2-top);
        width: var(--gift-tie-2-width);
        height: var(--gift-tie-2-height);
    }
</style>