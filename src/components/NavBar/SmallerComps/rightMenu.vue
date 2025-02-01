<template>
    <div class="container">
        <div class="left">
            <p>Navigation</p>
            <div class="nav-list">
                <ul>
                    <li>
                        <div class="dash"></div><span>Home</span>
                    </li>
                    <li>
                        <div class="dash"></div><span>Our Services</span>
                    </li>
                    <li>
                        <div class="dash"></div><span>About US</span>
                    </li>
                    <li>
                        <div class="dash"></div><span>Portfolio</span>
                    </li>
                    <li>
                        <div class="dash"></div><span>Reviews</span>
                    </li>
                    <li>
                        <div class="dash"></div><span>Contact Us</span>
                    </li>

                </ul>
            </div>
        </div>
        <div class="right">
            <div class="socials">
                <a href="">WhatsApp</a>
                <a href="">Telegram</a>
                <span class="email">hello@damacreativ.com</span>
            </div>
            <div class="policy">
                <span>Privacy Policy & Cookies</span>
                <span>© Dama 2025</span>
            </div>
        </div>

    </div>
</template>

<style lang="scss" scoped>
.container {
    height: 100%;
    display: flex;
    color: white;
    @media screen and (max-width: 768px) {
        flex-direction: column;
        gap: 9rem;
        
    }

    .left {
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        width:70%;
        @media screen and (max-width: 768px) {
            width:100%;
            height:fit-content;

            justify-content: flex-start;
            gap:5rem;
            
        }
        p{
            color:$grey;
        }

        // gap:4rem;
        .nav-list {
            ul {
                list-style-type: none;
                counter-reset: li-counter;

                li {

                    margin: 0.5rem 0;
                    font-size: clamp(3.5rem, 5vw, 5.5rem);
                    letter-spacing: 0.1rem;;
                    font-weight: 500;
                    cursor: pointer;
                    counter-increment: li-counter;
                    display: flex;
                    align-items: center;
                    

                    .dash {
                        width: 0rem;
                        height: 0.7rem;
                        background-color: white;
                        margin-right: 0.5rem;
                        transform: scaleX(0);
                        transform-origin: left;

                        transition: all 0.4s;


                    }

                    >span {
                        position: relative;

                        &::after {
                            content: counter(li-counter, decimal-leading-zero);
                            position: absolute;
                            top: 20%;
                            left: 100%;
                            font-size: 1rem;
                            font-weight: 300;
                            color:$grey;

                        }


                    }

                    &:hover {
                        .dash {
                            width: 4rem;
                            transform: scaleX(1);
                            transition: all 0.4s;
                        }
                    }
                }
            }
        }
    }
    .right{
        flex-grow: 1;
        display: flex;
        flex-direction: column;
        justify-content: flex-end;
        gap:2rem;
        @media screen and (max-width: 768px) {
            width:100%;
            justify-content: flex-start;
            gap:2rem;
            
        }
        .socials{
            display: flex;
            flex-direction: column;
            // align-items: center;
            a{
                color: white;
                text-decoration: none;
                font-size: 3rem;
            }
            .email{
                font-size: 1.5rem;
                color:$grey;
            }
          
        }
        .policy{
                span{
                    margin-bottom:0.5rem;
                    color:$grey;
                    display: block;
                }
            }

    }

}
</style>