### 실행화면

![project](https://github.com/qkrgudals1030/teamAI/assets/50895124/66b499a0-cf81-4e27-80ca-01cdff3533d7)


#### css파일
```
body {
    margin: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    height: 100vh;
    justify-content: center;
    background-color: black;
    overflow: hidden;
}

.image-container {
    width: 200px;
    height: 200px;
    transform-style: preserve-3d;
    transform: perspective(1000px) rotateY(0deg);
    transition: transform .7s;
}

.image-container span {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    transform: rotateY(calc(var(--i) * 90deg)) translateZ(400px);
}

.image-container span img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
  aspect-ratio: 1/1;
  -o-object-fit: cover;
     object-fit: cover;
  filter: grayscale(100%);

}

.btn-container {
    position: relative;
    width: 80%;
}

.btn {
  position: absolute;
  bottom: -140px;
  background-color: slateblue;
  color: white;
  border: none;
  padding: 10px 30px;
  border-radius: 5px;
  cursor: pointer;
  font-size: 20px;
}


.btn:hover {
    filter: brightness(1.5);
}

.image-container span img:hover {
  filter: none;
}

#prev {
    left: 20%;
}

#next {
    right: 20%;
}
```

#### html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>3D Image Carousel with Reflection</title>
    <style>
        body {
            margin: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            background: linear-gradient(135deg, #2b2b2b, #1a1a1a);
            overflow: hidden;
            color: white;
            font-family: 'Arial', sans-serif;
        }

        .carousel-container {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .image-container {
            width: 300px;
            height: 300px;
            position: relative;
            transform-style: preserve-3d;
            transform: perspective(1000px) rotateY(0deg);
            transition: transform 0.7s ease-in-out;
        }

        .image-container span {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            transform: rotateY(calc(var(--i) * 90deg)) translateZ(150px);
            backface-visibility: hidden;
        }

        .image-container span img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: 10px;
            box-shadow: 0 10px 20px rgba(255, 255, 255, 0.3), 0 0 20px rgba(255, 255, 255, 0.2);
            transition: transform 0.3s, filter 0.3s, box-shadow 0.3s;
            filter: grayscale(100%) brightness(0.9);
        }

        .image-container span img:hover {
            transform: scale(1.1);
            filter: grayscale(0%) brightness(1);
            box-shadow: 0 10px 20px rgba(255, 255, 255, 0.8), 0 0 30px rgba(255, 255, 255, 0.6);
        }

        .reflection-container {
            position: absolute;
            top: 100%;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            pointer-events: none;
        }

        .reflection {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 100%;
            transform: scaleY(-1);
            opacity: 0.4;
            filter: blur(5px);
        }

        .btn-container {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            width: 70%;
            display: flex;
            justify-content: space-between;

        }

        .btn {
            background-color: slateblue;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 20px;
            transition: background-color 0.3s, transform 0.3s;
        }

        .btn:hover {
            background-color: darkslateblue;
            transform: scale(1.1);
        }

        #prev {
            margin-right: auto;
        }

        #next {
            margin-left: auto;
        }
    </style>
</head>
<body>
    <div class="carousel-container">
        <div class="image-container">
            <span style="--i: 0">
                <img src="https://ssl.pstatic.net/static/nid/account/naver_og_image.png" class="clickable" data-url="https://www.naver.com">
                <div class="reflection-container">
                    <img src="https://ssl.pstatic.net/static/nid/account/naver_og_image.png" class="reflection" alt="Reflection">
                </div>
            </span>
            <span style="--i: 1">
                <img src="https://blog.google/static/blogv2/images/google-1000x1000.png" class="clickable" data-url="https://www.google.com">
                <div class="reflection-container">
                    <img src="https://blog.google/static/blogv2/images/google-1000x1000.png" class="reflection" alt="Reflection">
                </div>
            </span>
            <span style="--i: 2">
                <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/ae/Github-desktop-logo-symbol.svg/2048px-Github-desktop-logo-symbol.svg.png" class="clickable" data-url="https://github.com/qkrgudals1030/teamAI">
                <div class="reflection-container">
                    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/ae/Github-desktop-logo-symbol.svg/2048px-Github-desktop-logo-symbol.svg.png" class="reflection" alt="Reflection">
                </div>
            </span>
            <span style="--i: 3">
                <img src="https://www.youtube.com/img/desktop/yt_1200.png" class="clickable" data-url="https://www.youtube.com">
                <div class="reflection-container">
                    <img src="https://www.youtube.com/img/desktop/yt_1200.png" class="reflection" alt="Reflection">
                </div>
            </span>
        </div>
        <div class="btn-container">
            <button class="btn" id="prev">&larr; Prev</button>
            <button class="btn" id="next">Next &rarr;</button>
        </div>
    </div>

    <script>
        const imageContainerEl = document.querySelector(".image-container");
        const prevEl = document.getElementById("prev");
        const nextEl = document.getElementById("next");
        const clickableEls = document.querySelectorAll(".clickable");

        let x = 0;
        let timer;

        prevEl.addEventListener("click", () => {
            x += 90;
            clearTimeout(timer);
            updateGallery();
        });

        nextEl.addEventListener("click", () => {
            x -= 90;
            clearTimeout(timer);
            updateGallery();
        });

        clickableEls.forEach(el => {
            el.addEventListener("click", () => {
                const url = el.getAttribute("data-url");
                window.open(url, '_blank');
            });
        });

        function updateGallery() {
            imageContainerEl.style.transform = `perspective(1000px) rotateY(${x}deg)`;
            timer = setTimeout(() => {
                x -= 90;
                updateGallery();
            }, 3000);
        }

        updateGallery();
    </script>
</body>
</html>
```

#### js
```
const imageContainerEl = document.querySelector(".image-container");
const prevEl = document.getElementById("prev");
const nextEl = document.getElementById("next");
const clickableEls = document.querySelectorAll(".clickable");

let x = 0;
let timer;

prevEl.addEventListener("click", () => {
    x += 90;
    clearTimeout(timer);
    updateGallery();
});

nextEl.addEventListener("click", () => {
    x -= 90;
    clearTimeout(timer);
    updateGallery();
});

function updateGallery() {
    imageContainerEl.style.transform = `perspective(1000px) rotateY(${x}deg)`;
    timer = setTimeout( () => {
        x -= 90;
        updateGallery();
    }, 3000)
}
updateGallery();
```

### 소감 

박형민: 이번 팀과제를 통해 지금까지 유튜브영상을 통해 배웠던 내용을 활용해 저희만의 작품을 만들어 보면서 지금까지 했던 내용을 복습해 볼 수 있는 시간을 가질 수 있었고 저희가 배웠던 내용 뿐 아니라 다른사람들이 사용했던 내용들을 활용해 저희의 작품에 적용해 보면서 다양한 응용 방법에 대해서도 공부할 수 있었습니다. 또한 저 혼자 작품을 만드는 것이 아닌 팀원들과 함께 만들어 보면서 서로가 모르는 부분에서는 알려주고 잘맞지 않은 부분은 대화를 통해 해결해 보면서 좋은 결과물을 도출해낼 수 있었습니다. 이 팀과제로만 만족하는 것이 아닌 다양한 프로그램을 제작해 보면서 저만의 프로그램을 만들 수 있도록 열심히 공부해 볼 것입니다. ai그래픽스 화이팅!!!!!!!

손정우: 이번 r3f 마지막강의까지 들으면서 드는 생각은 우리가 지금까지 보는 그래픽들이 이런식으로 처음부터 만들어지는구나 하는 생각이 들었습니다. 제가 이번에 실습한것들은 극히 일부일지 모르지만 좋은 경험이 되었습니다. 실습뿐만아니라 지금까지 배운것들로 팀과제를 진행하였는데 팀원들이랑 수업시간 말고도 주말에 시간을 할애하여 다같이모여 주제부터 코드까지 같이 의논하여 역할 분담을 하였습니다. 저는 이미지를 물체에 넣었고 클릭하면 새로운 창을 넣어 페이지로 이동하는 과정을 했습니다. 예전부터 다뤄보고 싶었던 리엑트를 통해 팀과제부터 실습까지 해보니 도움이 되었고 깃허브에 팀장 리퍼지토리를 포크하여 진행하니 팀과제하는 맛이 있었습니다. 감사합니다.

박준범: 큐브를 회전시키고 면을 클릭하여 다른 사이트로 이동하는 기능을 만들어보니 흥미로웠습니다. R3F를 사용하여 3D 환경을 만들고 상호작용하는 부분을 구현하는 과정은 즐거웠습니다. 사용자가 면을 클릭하여 다른 사이트로 이동하는 경험은 직관적이고 흥미로웠습니다. 코드를 작성하면서 문제를 해결하는 과정에서 새로운 것을 배우고 성장하는 느낌을 받았습니다. 결과물의 가독성을 높이기 위해 코드를 정리하고 주석을 추가하는 작업이 중요했습니다. 마지막으로, 이 프로젝트를 통해 웹 개발 및 3D 그래픽에 대한 관심이 더욱 높아졌습니다.

김준영: 

