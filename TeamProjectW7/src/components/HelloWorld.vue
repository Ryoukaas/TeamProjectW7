<template>
    <!--Kat and Logans Project CIS235 2/23/203-->
    <div style="margin:auto; width:450px;">
        <!--It was decided that maybe too much rainbow was a thing so a toggle was made!-->
        <button class="btn" @click="show = !show">
            <!--Please don't miss this button, it's a good button to click-->
        <p v-if="show">Click me for blessed visual silence.</p>
        <p v-if="!show">Ok gimme back the rainbow blocks.</p>
        </button>
    </div>
    <!--This is the acid trip mouseMove that changes all the div colors-->
    <div @mousemove="onMousemove"
         :style="{ backgroundColor: `hsl(${x}, 80%, 50%)` }"
         class="movearea">

        <p class="hoverMeBig" style="color:white;">{{msg}}</p>
        <p v-if="size" style="color:white">The kitty below likes clicks, its a purring machine!</p>

    </div>
    <div :class="{ shake: disabled }">
        <!--All of the pictures are in here because if you click the black kitty, it will mmake ALL of these shake if they are currently rendered.-->
        <button class="btn" @click="warnDisabled">
            <Transition name="sizeS"><img v-if="size" src="../assets/BlackMeow.jpg" /> </Transition>
        </button>

        <Transition name="kittySPIN"><img v-if="kitty" src="../assets/StaringKitty.jpeg" /></Transition>

        <Transition name="corgiUpset"><img v-if="corgiAngry" src="../assets/angry_corgi.jpg" /></Transition>

        <Transition name="corgiHappy"><img v-if="corgiHaps" src="../assets/happy_corgi.jpg" /></Transition>

        <Transition name="playCorgi"><img v-if="corgiPlay" src="../assets/corgi_play.jpg"/></Transition>
    </div>
    <div v-if="show" style="margin:auto">
      
        <!-- Logan has since filled up the boxes that were empty -->
        <br />
        <!--This is the start of the mini rainbow boxes  with click events. -->
        <div @mousemove="onMousemove"
             :style="{ backgroundColor: `hsl(${x}, 80%, 50%)` }"
             class="movearea move1">
            <button class="btn white" @click="size = !size">Click me!</button>

        </div>
        <br />
        <div @mousemove="onMousemove"
             :style="{ backgroundColor: `hsl(${x}, 80%, 50%)` }"
             class="movearea move2">
            <button class="btn white" @click="kitty =!kitty">No, Click Me!!</button>
        </div>
        <br />
        <div @mousemove="onMousemove"
             :style="{ backgroundColor: `hsl(${x}, 80%, 50%)` }"
             class="movearea move3">
            <button class="btn white" @click="corgiAngry =!corgiAngry"> Want To See a Corgi!?</button>

        </div>
        <br />
        <div @mousemove="onMousemove"
             :style="{ backgroundColor: `hsl(${x}, 80%, 50%)` }"
             class="movearea move4">
            <button class="btn white" @click="corgiHaps =!corgiHaps"> What's behind this button??</button>

        </div>
        <br />
        <div @mousemove="onMousemove"
             :style="{ backgroundColor: `hsl(${x}, 80%, 50%)` }"
             class="movearea move5">
            <button class="btn white" @click="corgiPlay =!corgiPlay"> Play Time!</button>

        </div>
        <br />
        <div @mousemove="onMousemove"
             :style="{ backgroundColor: `hsl(${x}, 80%, 50%)` }"
             class="movearea move6">
            <p v-if="bark" style="color:white"><em>Bark bark!</em></p>
        </div>
        <br />
        <div @mousemove="onMousemove"
             :style="{ backgroundColor: `hsl(${x}, 80%, 50%)` }"
             class="movearea move7">
            <button class="btn" @click="bark =!bark"><img src="../assets/Dw4vhOaU0AwfOGj.png" style="width:50px; height:50px;" /></button> 
        </div>
    </div>

    <!--This is the reaction to the top blessed silence button-->
    <div v-if="!show" style="margin:auto;">
        <button @click="psyke =!psyke">
        <p v-if="psyke">No seriously, stop.</p>
            <p v-if="!psyke">ALL HAIL HYPNOTOAD.</p>
        </button>
        <div v-if="psyke">
            <p>
            <b>
                PSYKE! GIVE HYPNO TOAD ALL YOUR POINTS.
                </b>
            </p>
            <img src="../assets/rainbow-frog-5.gif" />

            <p>I'm sure you get the reference but here have an embed!</p>

            <!--Kat: I got a little too excited about finding such an amazing rainbow gif of hypno toad-->
            <iframe width="560" height="315" src="https://www.youtube.com/embed/CDsIlAXWORw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
        </div>
        <div v-if="!psyke" style="margin:auto;">
            <p class="hoverMeLittle">Fiiiine :(</p>

        </div>
    </div>
    
    <br />









</template>
<!--Kat: I stole some scripts from https://vuejs.org/guide/extras/animation.html for trigger testing I modified them a bit
    the color one was changed to use the Y axis and the timer for the shake was shortened more. I also made an infinite spinning box loop that originally went 
    in a 4 square rotation, it was annoying to look at. You're Welcome.-->


<!--Here is all our variables for the various vue based animations/transitions-->
<script>
    export default {
        name: 'HelloWorld',
        props: {
            msg: String,
            show: Boolean
        },
        data() {
            return {
                disabled: false,

                x: 0,
                show: true,
                size: true,
                kitty: false,
                psyke: true,
                bark: false,
                corgiAngry: false,
                corgiHaps: false,
                corgiPlay: false
            }
        },
        methods: {
            warnDisabled() {
                this.disabled = true
                setTimeout(() => {
                    this.disabled = false
                }, 500)
            },
            onMousemove(e) {
                this.x = e.clientY
            }
        }
    }
</script>

<!--This is the start of ALL the animation adn CSS-->

<style>
    /*
       htmml,body was the background. .btn was ripped for w3schoools so that pictures didnt have weird boarders when they are used as buttons.
    */
    html,
    body {
        background-color: bisque
    }

    .btn {
        border: none;
        background-color: inherit;
        padding: 14px 28px;
        font-size: 16px;
        cursor: pointer;
        display: inline-block;
    }

    .white {
        color: white;
    }
    /*
        hoveMe of any kind involved text manipulation, the names are self explanetory.
    */
    .hoverMeBig {
        font-size: 14px;
        transition-property: font-size;
        transition-duration: 4s;
    }

        .hoverMeBig:hover {
            font-size: 36px;
        }

    .hoverMeLittle {
        font-size: 14px;
        transition-property: font-size;
        transition-duration: 4s;
    }

        .hoverMeLittle:hover {
            font-size: 6px;
        }

    /*Another thing taken from vue animations page this is what makes kitty "purr"*/
    .shake {
        animation: shake 0.82s cubic-bezier(0.36, 0.07, 0.19, 0.97) both;
        transform: translate3d(0, 0, 0);
    }

    @keyframes shake {
        10%, 90% {
            transform: translate3d(-1px, 0, 0);
        }

        20%, 80% {
            transform: translate3d(2px, 0, 0);
        }

        30%, 50%, 70% {
            transform: translate3d(-4px, 0, 0);
        }

        40%, 60% {
            transform: translate3d(4px, 0, 0);
        }
    }
    /*Kat: I have a weird.... color idea, it may hurt the eyes, sorry.

        EDIT: It did hurt the eyes. But I toned it down. This is the css for the rainbow boxes
    */
    .movearea {
        transition: 0.6s background-color ease;
        width: 650px;
        height: 100px;
        margin: auto;
    }

    /*
        Kitty shrinker 9000
    */
    .sizeS-enter-active,
    .sizeS-leave-active {
        transition-property: transform;
        transition-duration: 3s;
    }

    .sizeS-enter-from,
    .sizeS-leave-to {
        transform: scale(0.3);
    }

    /*Kitty barfer 12,000*/
    .kittySPIN-enter-active,
    .kittySPIN-leave-active {
        transition-property: transform;
        transition-duration: 3s;
    }

    .kittySPIN-enter-from,
    .kittySPIN-leave-to {
        transform: rotate(-360deg);
    }


    /* Corgis all barfing IN REVERSE*/
    .corgiUpset-enter-active,
    .corgiUpset-leave-active {
        transition-property: transform;
        transition-duration: 3s;
    }

    .corgiUpset-enter-from,
    .corgiUpset-leave-to{
        transform: rotate(-360deg);
    }

    .corgiHappy-enter-active,
    .corgiHappy-leave-active {
        transition-property: transform;
        transition-duration: 3s;
    }

    .corgiHappy-enter-from,
    .corgiHappy-leave-to {
        transform: rotate(-360deg);
    }
    /* Projectile barfing corgi*/
    .playCorgi-enter-active,
    .playCorgi-leave-active{
        transition-property: transform;
        transition-duration: 3s;
    }
 
    .playCorgi-enter-from,
    .playCorgi-leave-to{
        transform: rotate(360deg);
    }
    /*All of these moves are the animation timing and delay for each rainbow box*/
    .move1 {
        width: 300px;
        height: 100px;
        position: relative;
        animation: linear;
        animation-name: moveBox;
        animation-duration: 7s;
        animation-iteration-count: infinite;
       
    }

    .move2 {
        width: 300px;
        height: 100px;
        position: relative;
        animation: linear;
        animation-name: moveBox;
        animation-delay: 2s;
        animation-duration: 7s;
        animation-iteration-count: infinite;
      
    }


    .move3 {
        width: 300px;
        height: 100px;
        position: relative;
        animation: linear;
        animation-name: moveBox;
        animation-delay: 3s;
        animation-duration: 7s;
        animation-iteration-count: infinite;
       
    }

    .move4 {
        width: 300px;
        height: 100px;
        position: relative;
        animation: linear;
        animation-name: moveBox;
        animation-delay: 4s;
        animation-duration: 7s;
        animation-iteration-count: infinite;
    
    }

    .move5 {
        width: 300px;
        height: 100px;
        position: relative;
        animation: linear;
        animation-name: moveBox;
        animation-delay: 5s;
        animation-duration: 7s;
        animation-iteration-count: infinite;
     
    }

    .move6 {
        width: 300px;
        height: 100px;
        position: relative;
        animation: linear;
        animation-name: moveBox;
        animation-delay: 6s;
        animation-duration: 7s;
        animation-iteration-count: infinite;
    
    }

    .move7 {
        width: 300px;
        height: 100px;
        position: relative;
        animation: linear;
        animation-name: moveBox;
        animation-delay: 7s;
        animation-duration: 6s;
        animation-iteration-count: infinite;
     
    }
    /*Rainbow box keyframes*/
    @keyframes moveBox {
        0% {
            left: 0px;
            top: 0px;
        }

        25% {
            left:300px;
          
        }
        48%{
            transform: rotateY(90deg);
        }
        50% {
            left:300px;
            
        }
        75%{
            transform: rotateY(-90deg);
        }
        100% {
            left: 0px;
            
        }
    }
</style>
