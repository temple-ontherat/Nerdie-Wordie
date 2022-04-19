<!DOCTYPE html>
<html lang="en"><head>
<meta http-equiv="content-type" content="text/html; charset=UTF-8">
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wordie</title>
</head>
<body>
    <p id="secret">&nbsp;</p>
    
    <h2>The object of this game is to guess a secret word. The secret word has five letters that don't repeat.
        Try to guess it by entering a similar word. With each word you guess you will be
        given a hint in the following format: </h2>
        <h3><b>(common letters in the same place) : (common letters in different places)</b></h3>
        <h3>Here's an example: if the secret word is horse and you guess crust, the hint is (s):(r) .</h3>
        <h3>Type in your guess and press the button.</h3>
    <p id="attempts">Number of attempts:</p> 
    <h3 id="success"></h3>
    <p id="poop"></p>
    

    <input id="guess" type="text">
    <input type="button" value="guess" onclick="doResult()">
 
    <script type="text/javascript">
        attempts=0
        const secret = ['sword', 'fibre', 'heavy', 'dream', 'thank', 'mercy', 'steam', 'study', 'stamp', 'relax', 'draft', 'brown',
            'virus', 'noble', 'stain', 'brick', 'truck', 'trick', 'haunt', 'glory', 'brush', 'motif', 'spoil', 'cover',
            'pride', 'mouse', 'first', 'money', 'march', 'shame', 'laser', 'major', 'plane', 'unity', 'angle', 'field',
            'wrong', 'death', 'voter', 'smart', 'chain', 'bowel', 'split', 'wreck', 'style', 'cover', 'adult', 'flock',
            'flesh', 'ample', 'chaos', 'study', 'build', 'graze', 'print', 'cable', 'trunk', 'tiger', 'space', 'basic',
            'ideal', 'build', 'elbow', 'admit', 'quota', 'quest', 'slant', 'stamp', 'flush'];
        var randomNumber = Math.floor((Math.random() * secret.length) + 1); //picks a random number between 1 and the number of secret words in library   
        var secretWord = secret[randomNumber];
      //  document.getElementById("guess").value="";
        var result = "You guessed it!";
        var warning = "Your guess must be a 5-letter word with no repeating letters.";
        tries =""
        var samesame="";
        var samelet="";
        var hint="";
    
      //  document.getElementById("secret").innerHTML= secretWord;
        function doResult() {
          //  document.getElementById("guess").select();
            document.getElementById("poop").innerHTML= "";//display entries
            samesame=""; samelet=""
            var guess = document.getElementById("guess").value.toLowerCase();
            
            if (guess.length != 5) {
            document.getElementById("poop").innerHTML= warning;//display entries
            document.getElementById("guess").value="";
            return;
            //clear box
            } for (i=0; i<5; i++) {
                if (guess.charAt(i)==secretWord.charAt(i)) {
                    samesame+=guess.charAt(i);
                } else if (secretWord.includes(guess.charAt(i))) {
                    samelet+=guess.charAt(i);
                }
            }
            hint="("+samesame+")"+":"+"("+ samelet+")";
            if (guess == secretWord) {//check for matching word
            document.getElementById("success").innerHTML= guess+"! "+result;//display message
            document.getElementById("guess").value="";//clear box
            
             }
            
            else {

            document.getElementById("success").innerHTML= tries+=guess+"-- " + hint+";  ";//display entries
            document.getElementById("guess").value="";//clear box
              }            
        attempts +=1;
        document.getElementById("attempts").innerHTML= "Number of attempts: " + attempts;//display # of tries
        
        return; 

            }

    
         
        

        
    </script>

</body></html>
