
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Pair Code</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      background: linear-gradient(135deg, #000000, #434343);
      overflow: hidden;
      font-family: Arial, sans-serif;
    }

    .matrix {
      position: absolute;
      width: 100%;
      height: 100%;
      overflow: hidden;
      z-index: -1;
      color: rgba(0, 255, 0, 0.5);
      font-size: 20px;
      font-family: monospace;
    }

    .matrix div {
      position: absolute;
      width: 20px;
      height: 100%;
      top: 0;
      animation: matrix-fall linear infinite;
    }

    @keyframes matrix-fall {
      0% {
        top: -100%;
      }
      100% {
        top: 100%;
      }
    }

    .container {
      display: flex;
      flex-direction: column;
      align-items: center;
      z-index: 1;
    }

    .box {
      width: 300px;
      height: 320px;
      padding: 20px;
      position: relative;
      text-align: center;
      background-color: rgb(0, 0, 0);
      border-radius: 10px;
      transform: perspective(1000px) rotateY(0deg);
      box-shadow: 0 0 20px rgba(250, 249, 249, 0.7);
    }

    #text {
      color: #f6f5f5;
    }

    .input-container input {
      color: #f1eaea;
    }

    .centered-text {
      color: #e9e4e4;
    }

    .input-container {
      display: flex;
      background: rgb(10, 10, 10);
      border-radius: 1rem;
      background: black;
      box-shadow: black;
      padding: 0.3rem;
      gap: 0.3rem;
      max-width: 300px;
      width: 100%;
    }

    .input-container input {
      border-radius: 0.8rem 0 0 0.8rem;
      background: #e8e8e8;
      box-shadow: inset 13px 13px 10px #dcdcdc, inset -13px -13px 10px #f4f4f4;
      width: 100%;
      flex-basis: 75%;
      padding: 1rem;
      border: none;
      border-left: 2px solid #ecf2f8;
      color: #000000;
      transition: all 0.2s ease-in-out;
    }

    .input-container input:focus {
      border-left: 2px solid #ecf1f6;
      outline: none;
      box-shadow: inset 13px 13px 10px #f0f2f3, inset -13px -13px 10px #f4f4f4;
    }

    .input-container button {
      flex-basis: 15%;
      padding: 1rem;
      background: #000000;
      font-weight: 700;
      letter-spacing: 0.3rem;
      text-transform: uppercase;
      color: white;
      border: 2px solid red;
      width: 90%;
      border-radius: 0 1rem 1rem 0;
      transition: all 0.2s ease-in-out;
    }

    .input-container button:hover {
      background-color: red;
      border-color: green;
    }

    @media (max-width: 500px) {
      .input-container {
        flex-direction: column;
      }

      .input-container input {
        border-radius: 0.8rem;
      }

      .input-container button {
        padding: 0.4rem;
        border-radius: 0.8rem;
      }
    }

    .centered-text {
      text-align: center;
    }

    @media (max-width: 500px) {
      .box {
        width: 90%; 
      }
    }

    @media (max-width: 500px) {
      .input-container input {
        border-radius: 0.8rem;
        width: 80%; 
      }

      .input-container button {
        padding: 1rem;
        border-radius: 0.9rem;
        width: 100%; 
      }
    }
  </style>
</head>
<body>
  <div class="matrix"></div>
  <div class="container">
    <div class="main">
      <div class="box" id="box">
        <div id="text">
          <i class="fa fa-user"></i>
          <p>
            <h3 class="centered-text">X-V2-MD PAIRING CODE</h3>
            <br>
            <h6>Made By David Cyril⚡.</h6>
            <h6>Enter Your Number with Country Code.</h6>
            <div class="input-container">
              <input placeholder="234906652xxx" type="number" id="number" placeholder="Enter your Phone Number with Country Code" name="">
              <button id="submit">Submit</button>
            </div>
            
            <a id="waiting-message" class="centered-text" style="display: none;">Please wait a while</a>
            <br>
            <br>
            <main id="pair"></main>
          </p>
        </div>
      </div>
    </div>
  </div>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/axios/1.0.0-alpha.1/axios.min.js"></script>
  <script>
    let a = document.getElementById("pair");
    let b = document.getElementById("submit");
    let c = document.getElementById("number");

    async function Copy() {
      let text = document.getElementById("copy").innerText;
      let obj = document.getElementById("copy");
      await navigator.clipboard.writeText(obj.innerText.replace('CODE: ', ''));
      obj.innerText = "COPIED";
      obj.style = "color:blue;font-weight:bold";
      obj.size = "5";
      setTimeout(() => {
        obj.innerText = text;
        obj.style = "color:white;font-weight:bold";
        obj.size = "5";
      }, 500);
    }

    b.addEventListener("click", async (e) => {
      e.preventDefault();
      if (!c.value) {
        a.innerHTML = '<a style="color:white;font-weight:bold">Enter your WhatsApp number with Country Code</a><br><br>';
      } else if (c.value.replace(/[^0-9]/g, "").length < 11) {
        a.innerHTML = '<a style="color:red;font-weight:bold">Invalid Number</a><br><br>';
      } else {
        const Wasi_Tech = c.value.replace(/[^0-9]/g, "");
        let bb = "";
        let bbc = "";
        const cc = Wasi_Tech.split('');
        cc.map(a => {
          bbc += a;
          if (bbc.length == 3) {
            bb += " " + a;
          } else if (bbc.length == 8) {
            bb += " " + a;
          } else {
            bb += a;
          }
        });
        c.type = "text";
        c.value = "+" + bb;
        c.style = "color:black;font-size:20px";
        a.innerHTML = '<a style="color:white;font-weight:bold">Please Wait...</a><br><br>';
        let { data } = await axios(`/code?number=${Wasi_Tech}`);
        let code = data.code || "Service Unavailable";
        a.innerHTML = '<font id="copy" onclick="Copy()" style="color:red;font-weight:bold" size="5">CODE: <span style="color:white;font-weight:bold">' + code + '</span></font><br><br><br>';
      }
    });

    function createMatrix() {
      const matrixContainer = document.querySelector('.matrix');
      const columns = Math.floor(window.innerWidth / 20);
      for (let i = 0; i < columns; i++) {
        const column = document.createElement('div');
        column.style.left = `${i * 20}px`;
        column.style.animationDuration = `${Math.random() * 5 + 2}s`;
        matrixContainer.appendChild(column);

        for (let j = 0; j < 30; j++) {
          const char = document.createElement('span');
          char.innerText = String.fromCharCode(0x30A0 + Math.random() * 96);
          column.appendChild(char);
        }
      }
    }

    createMatrix();
  </script>
</body>
</html>
