<template>

    <div class="our-clients-container">
        <h1 class="sectionHeader">04. Our Clients</h1>

        <div class="our-clients-wrapper">
            <div class="left"><p class="sectionText">
                We work with clients across the
entire globe to elevate their marketing game and drive real results.
            </p>
        <img src="/images/clients/behance.png" alt="Our Clients">
        </div>
            <div class="right">

            </div>
        </div>

    </div>

</template>
<style lang="scss" scoped>
.our-clients-container {
    @include sectionPadding;
    .our-clients-wrapper {
        display: flex;
        padding:1rem 0;
        .left {
            display:flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }
    }
}
</style>