<template>
    <div class="game">
    <nav class="nav">
        <h1>Speed Typing Game</h1>
    </nav>

    <section class="level">
        <h2>Select Level</h2>
        <button @click="easyLevel">Easy</button>
        <button @click="mediumLevel">Medium</button>
        <button @click="hardLevel">Hard</button>
    </section>
    <section class="content">
        <h3>Type the given word within <span class="seconds">{{seconds}}</span> seconds</h3>
        <h1>{{currentWord}} </h1>
            <form ref="form" @submit.prevent="getValue(),addScore()" >
                <input type="text" placeholder="Start typing" v-model="input" name="inputValue" />
            </form>

        <h4 class="message">{{message}}</h4>
        <div class="score">
        <h4>Time Left: {{time}}</h4>
        <h4>Score: {{score}}</h4>
        

        </div>

        <button class="newGame" @click="refresh">New Game</button>
    </section>
    <footer>
        <h5>Instructions</h5>
        <p>
        Type each word in the given amount of seconds to score. To play, just
        type the current word. Your score will reset
        </p>
    </footer>
    </div>
</template>

<script>
export default {
    name: "game",
    data() {
    return {
    seconds: 0,
    easy: 7,
    medium: 5,
    hard: 3,
    currentLevel: '',
     input: '',
    message: '',
    isPlaying: true,
   currentWord: '',
   time: 0,
   score: 0,
    words:[
'hello',
'amycruz',
'lizibikey',
'hat',
'river',
'statue',
'generate',
'stubborn',
'cocktail',
'sugar',
'nonsense',
'jealous',
'impatient',
'joke',
'css',
'vue',
'javascript',
'algorithm',
"own",
"other",
"old",
"right",
"big",
"high",
"different",
"small",
"large",
"next",
"early",
"young",
"important",
"few",
"public",
"bad",
"same",
"able"



    ],

    };
    },
    // watch:{
    //     gameOver(){
    //         if(this.countDown() === 1){
    //             console.log('game over')

    //     }
    //     }
      

    // },

    methods: {
        

    easyLevel() {
        this.seconds = this.easy;
        this.displayTime();
        this.countDown();
        


    },
    mediumLevel() {
        this.seconds  = this.medium;
        this.displayTime()
        this.countDown()

    },
        hardLevel() {
        this.seconds = this.hard;
        this.displayTime()
        this.countDown()
        
        

    },

    getValue() {
        const inputValues = this.$refs.form.inputValue.value;
        if(inputValues === this.currentWord){
            this.message = 'CORRECT'
            this.currentWord = this.getRandomWord()
            this.input = '';
            this.score++
            this.resetTimer()
            
           
        }else{
            this.message = 'Wrong Answer'
        }
    },
        displayTime(){
            this.time = this.seconds
        },

    countDown(){

        setInterval(()=>{
        let countDownTime = this.time

        if(countDownTime > 0){
            this.time--

        }else{
            this.isPlaying = false
            this.message = 'Gameover'
            this.input =''
          
        }

        }, 1200)

    },

    resetTimer(){
    clearInterval(this.countDown())
    },
    addScore(){
        let inputValue = this.$refs.form.inputValue.value;
            if(inputValue === this.currentWord){
            this.words
            
            
        }

    // if (this.score === -1) {
    //     this.score = 0;
	// } else {
	// this.score 
	// }

    },

   
 

    refresh(){
        window.location.reload();
    },

    getRandomWord(){
         let random = Math.floor(Math.random() * this.words.length)
        return this.words[random];



    }
    },


    mounted(){
        // let random = Math.floor(Math.random() * this.words.length)
        // this.currentWord = this.words[random];
        this.currentWord = this.getRandomWord()

        



    },
};
</script>





















<style scoped>
.nav {
    background-color: #0d0a0b;
 padding: 2px;
    margin-top: -2rem;
}
h1,
h2,
h3 {
    color: #fff;
    padding-top: 1rem;
    font-size: 2rem;
    font-weight: bold;
}

.level button {
    background: #ff1053;
    padding: 0.5rem 2rem;
    outline: none;
    border-radius: 5px;
    border: 1px solid #454955;
    margin-right: 2rem;
    color: #fff;
    font-size: 1rem;
    transition: all ease-in-out 300ms;
}

.level button:hover {
    background: #d81e5b;
    transform: translate(0px, -10px) scale(1.2);
    padding: 0.5rem 2rem;
}

.content {
    color: #fff;
}

.seconds {
    color: #d81e5b;
}
.content input {
    width: 45%;
    padding: 1rem;
    border-radius: 5px;
    border: 1px solid #fff;
    outline: #fff;
}

.score {
    display: flex;
    flex-direction: row;
    justify-content: center;
}
.score h4 {
    font-size: 2.5rem;
    margin-right: 3rem;
}

.newGame{
    background: #ff1053;
    padding: 0.7rem 2.5rem;
    outline: none;
    border-radius: 5px;
    border: 1px solid #454955;
}

footer {
    background: #0d0a0b;
    width: 45%;
    height: 30%;
    padding: 1.5rem;
    border-radius: 5px;
    margin: auto;
    color: #fff;
    margin-top: 4rem;
}
</style>
