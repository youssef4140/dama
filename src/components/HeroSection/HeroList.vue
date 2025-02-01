<template>
    <div class="hero_list">
        <ul>
            <li>Home</li>
            <li>About us</li>
            <li>Our Services</li>
            <li>Portfolio</li>
            <li>Contact Us</li>
            <li>Reviews</li>
        </ul>
    </div>
</template>

<style lang="scss" scoped>
.hero_list{
    ul{
        display: flex;
        flex-direction: column;
        gap:1rem;
        list-style: none;
        padding: 1rem;
        margin-bottom:6rem;
        color:$darkLilac;
        li{
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: end;
            font-size: 1.2rem;
            &:hover{
                color: $lilac;
            }
        }
    }
}
</style>