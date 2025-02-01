<template>
    <div class="hero_nav">
        <div class="logo"><img src="/images/Logo.png" alt="logo" />
        </div>
        <div class="nav_list">
            <ul>
                <li>
                    <span class="fst">About us</span>
                    <span class="snd">About us</span>
                </li>
                <li>
                    <span class="fst">Cases</span>
                    <span class="snd">Cases</span>
                </li>
                <li>
                    <span class="fst">Reviews</span>
                    <span class="snd">Reviews</span>
                </li>
                <li>
                    <span class="fst">Contact Us</span>
                    <span class="snd">Contact Us</span>
                </li>
            </ul>
        </div>
        <div class="empty"></div>
    </div>
</template>

<style lang="scss" scoped>
.hero_nav {
    position: absolute;
    top: 0;
    width: 98%;
    padding:0 1.6rem;
    top: 3rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    z-index:1;
    // background-color: green;

    .logo,
    .empty {
        // min-height: 10px;
        background-color:transparent;
        width: 30%;
        display: flex;
        // align-items: center;
    }
    .empty {
        color:transparent;
    }

    .logo {
        
        img {
        width: 8rem;
        

        @media screen and (max-width: $maxWidth) {
            margin-top:1.2rem;

            
        }
    }}

    .nav_list {
        width: 30%;
        padding: 0 1rem;
        background-color: $lilac;
        border-radius: $radius;
        color: $black;

        @media screen and (max-width: $maxWidth) {
            display: none;

        }

        ul {
            display: flex;
            justify-content: space-around;
            list-style: none;
            padding: 1.2rem 1.5rem;

            li {
                // color: white;
                // background-color: green;
                cursor: pointer;
                overflow: hidden;
                position: relative;
                color: black;
                font-weight: 500;
                font-size: 1rem;

                .fst {
                    display: block;
                    transition: all 0.5s;

                }

                .snd {
                    position: absolute;
                    top: 100%;
                    left: 0;
                    transition: all 0.5s;

                }

                &:hover {
                    .fst {
                        transform: translatey(-100%);
                        transition: all 0.5s;

                    }

                    .snd {
                        top: 0;
                        transition: all 0.5s;

                    }
                }

            }
        }
    }
}
</style>