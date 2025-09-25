</title>
Final Puzzle! 
Drive to Linville Falls and DO NOT BE LATE -- you have to keep this secret! Dont even tell Sam if you solve this. A "Correct!" will appear when you have solved the cipher.
</title>
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Caesar Puzzle — Interactive</title>
  <style>
    body {
      margin: 0;
      background: #013220; /* dark green background */
      font-family: Arial, sans-serif;
      color: #f0f6f0;
      display: flex;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      padding: 20px;
    }
    .card {
      max-width: 820px;
      background: #0b2015;
      border-radius: 14px;
      padding: 28px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.6);
    }
    h1 { margin-top: 0; }
    p.instructions {
      background: rgba(255,255,255,0.05);
      padding: 12px;
      border-radius: 10px;
      font-size: 15px;
      line-height: 1.5;
    }
    .ciphertext {
      font-size: 20px;
      letter-spacing: 2px;
      margin: 20px 0;
      text-align: center;
      font-weight: bold;
    }
    .inputs {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
      justify-content: center;
      margin-bottom: 16px;
    }
    .inputs input {
      width: 32px;
      height: 40px;
      font-size: 18px;
      text-transform: uppercase;
      text-align: center;
      border: 1px solid rgba(255,255,255,0.2);
      background: rgba(255,255,255,0.08);
      color: #fff;
      border-radius: 6px;
    }
    .inputs input:disabled {
      background: transparent;
      border: none;
      width: 14px;
    }
    .result {
      font-size: 20px;
      font-weight: bold;
      text-align: center;
      margin-top: 12px;
      color: #9bd1ff;
      visibility: hidden;
    }
    .result a {
      color: #9bd1ff;
      text-decoration: underline;
    }
  </style>
</head>
<body>
  <div class="card">
    <h1>Caesar Cipher Puzzle</h1>
    <p class="instructions">
      Key clue: Count the letters in the word “Travel”.<br><br>
      The key is the number you get from the clue.<br><br>
      Shift each letter back in the alphabet by that many places (A→Z wrapping around) to decode the message.<br><br>
      Spaces are already in the right spots.<br>
    </p>

    <div class="ciphertext">UIZUHKX KRKBKT GZ ZKT GS</div>

    <div class="inputs" id="inputs"></div>

    <div class="result" id="result">
      Correct! 🎉 <br>
      <a href="https://docs.google.com/forms/d/e/1FAIpQLSduID_uf-AHlVmcFyGjqNXn4BtUrFzDdyUm1uv87f37Gk_h_Q/viewform?usp=header" target="_blank">
        Click here to continue
      </a>
    </div>
  </div>

  <script>
    // The correct decoded message (change if you want a different solution)
    const solution = "OCTOBER ELEVEN AT TEN AM";

    const container = document.getElementById("inputs");

    // Build inputs based on solution
    solution.split("").forEach(char => {
      if(char === " "){
        const spacer = document.createElement("input");
        spacer.disabled = true;
        spacer.value = " ";
        container.appendChild(spacer);
      } else {
        const box = document.createElement("input");
        box.maxLength = 1;
        box.dataset.correct = char;
        container.appendChild(box);
      }
    });

    const inputs = container.querySelectorAll("input:not([disabled])");
    const result = document.getElementById("result");

    function checkSolution(){
      let guess = "";
      container.querySelectorAll("input").forEach(el => {
        guess += el.value.toUpperCase() || (el.disabled ? " " : "");
      });
      if(guess === solution){
        result.style.visibility = "visible";
      } else {
        result.style.visibility = "hidden";
      }
    }

    inputs.forEach((input, i) => {
      input.addEventListener("input", () => {
        input.value = input.value.toUpperCase();
        if(input.value && i < inputs.length-1){
          inputs[i+1].focus();
        }
        checkSolution();
      });
    });
  </script>
</body>
</html>
