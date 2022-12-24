// Variables of slide images
let btn1 = document.querySelector(".radio1");
let btn2 = document.querySelector(".radio2");
let btn3 = document.querySelector(".radio3");
let btn4 = document.querySelector(".radio4");
let btns = document.querySelectorAll(".btns div")
let imgs = document.querySelector(".imgs");

// Loop of slide images
btns.forEach(ele => {
    ele.addEventListener('click', (e) => {

        handleActive(e);

    });
})

// Sitting box controller
btn1.onclick = function(){
    imgs.style.marginLeft = "0%";
};

btn2.onclick = function(){
    imgs.style.marginLeft = "-100%";
};

btn3.onclick = function(){
    imgs.style.marginLeft = "-200%";
};

btn4.onclick = function(){
    imgs.style.marginLeft = "-300%";
};

// Set color of site in local storage
let mainColor = localStorage.getItem("color_option");

// Set local storage information
if (mainColor !== null) {

    document.documentElement.style.setProperty('--main--color', mainColor);

    document.querySelectorAll(".list-options li").forEach(element => {

        element.classList.remove("play");

        if (element.dataset.color === mainColor) {
            element.classList.add("play");
        };

    });
};

// Random slide image controller
var counter = 0;
var change = 1;

let BackOption = true;

let optionRandom;

let localRandom = localStorage.getItem("random-option");

if (localRandom !== null) {

    if (localRandom === 'true'){
        
        BackOption = true;

    } else {

        BackOption = false;

    }

    document.querySelectorAll(".Random-option span").forEach(element => {

        element.classList.remove("on");

    });

    if (localRandom === 'true') {

        document.querySelector(".yes").classList.add("on");

    } else {

        document.querySelector(".no").classList.add("on");

    };

}

// Controller of slide box
function BackSitting() {

    if (BackOption === true) {

        optionRandom = setInterval(() => {
            imgs.style.marginLeft = -counter+"00%";
            counter++;
            if (counter == 4) {
                counter = 0;
            };
            if (change == 1) {
                btn1.classList.add("run");
            } else {
                btn1.classList.remove("run");
            }
            if (change == 2) {
                btn2.classList.add("run");
            } else {
                btn2.classList.remove("run");
            }
            if (change == 3) {
                btn3.classList.add("run");
            } else {
                btn3.classList.remove("run");
            }
            if (change == 4) {
                btn4.classList.add("run");
            } else {
                btn4.classList.remove("run");
            }
            change++;
            if (change == 5) {
                change = 1;
            }
        }, 10000);

    }

}
BackSitting();

// Making X menu
let sittingBox = document.querySelector(".sitting-box");

let right = document.querySelector(".right");

let left = document.querySelector(".left");

let middle = document.querySelector(".middle");

document.querySelector(".tools").onclick = function(e){

    e.stopPropagation();

    sittingBox.classList.toggle("open");

    right.classList.toggle("hide");

    left.classList.toggle("rotateY");

    middle.classList.toggle("rotateX");

};

document.addEventListener('click', (e) => {

    if (e.target !== document.querySelector(".tools")) {

        if (sittingBox.classList.contains("open")) {

            sittingBox.classList.remove("open");

            right.classList.remove("hide");

            left.classList.remove("rotateY");

            middle.classList.remove("rotateX");

        };

    };

});

// Set properties of main-color and local storage
const colorLi = document.querySelectorAll(".list-options ul li");

colorLi.forEach(li => {
    
li.addEventListener('click', (e) => {
    document.documentElement.style.setProperty('--main--color', e.target.dataset.color);

    localStorage.setItem("color_option", e.target.dataset.color);

    e.target.parentElement.querySelectorAll(".play").forEach(element => {

        element.classList.remove("play");
    });
    e.target.classList.add("play");
});
});

// Random option
const randomBack = document.querySelectorAll(".Random-option");

randomBack.forEach(span => {
    
span.addEventListener('click', (e) => {

    e.target.parentElement.querySelectorAll(".on").forEach(element => {

        element.classList.remove("on");
    });
    e.target.classList.add("on");


    if (e.target.dataset.background === "yes") {

        BackOption = true;

        BackSitting();

        localStorage.setItem("random-option", true)

    } else {

        BackOption = false;

        clearInterval(optionRandom);

        localStorage.setItem("random-option", false)

    }
    
});
});

// Make slide skills
let ourSkills = document.querySelector(".skills");

let start = false;

window.onscroll = function () {

    let skillsOffsetTop = ourSkills.offsetTop;

    let skillsOuterHeight = ourSkills.offsetHeight;

    let windowHeight = this.innerHeight;

    let windowScrollTop = this.pageYOffset;

    if (windowScrollTop > (skillsOffsetTop + skillsOuterHeight - windowHeight) ) {

        let allSkills = document.querySelectorAll(".skill-box .skill-progress span");

        allSkills.forEach(skill => {

            skill.style.width = skill.dataset.progress;

        });

        if (!start) {

            Num.forEach((ele) => IncreasNum(ele));

        }

        start = true;

    }

}; 

// Increasing number ratio
let Num = document.querySelectorAll(".skill-box .skill-progress div");

function IncreasNum(num) {

    let IncNum = num.dataset.number;

    let Run = setInterval(() => {

        num.textContent++;

        if (num.textContent == IncNum) {

            clearInterval(Run);

        }

    }, 10);

}


// Make popup gallery
let ourGalllery = document.querySelectorAll(".gallery img");

ourGalllery.forEach(img => {
    
    img.addEventListener('click', (e) => {

        let overlay = document.createElement("div");

        overlay.className = "popup-overlay";

        document.body.appendChild(overlay);

        let popupBox = document.createElement("div");

        popupBox.className = "popup-box";

        let closeButton = document.createElement("span");

        let buttonText = document.createTextNode("X");

        closeButton.appendChild(buttonText);

        popupBox.appendChild(closeButton);

        closeButton.className = "close-button";

        let popupImg = document.createElement("img");

        popupImg.src = img.src;

        popupBox.appendChild(popupImg);

        document.body.appendChild(popupBox);

        if (img.alt !== null) {

            let imageHeading = document.createElement("h2");

            let imageHeadingText = document.createTextNode(img.alt);

            imageHeading.appendChild(imageHeadingText);

            popupBox.appendChild(imageHeading);

            let imagesData = e.target.dataset.text;

            let imageText = document.createElement("p");

            let imageTextNode = document.createTextNode(imagesData);

            imageText.appendChild(imageTextNode);

            popupBox.appendChild(imageText);

        }

    });

});

// Remove popup
document.addEventListener('click', (e) => {

    if (e.target.className == "close-button") {

        e.target.parentNode.remove();

        document.querySelector(".popup-overlay").remove();

    }

})

// Select All Bullets
const allBullets = document.querySelectorAll(".nav-bullets .bullets");

const allLinks = document.querySelectorAll(".links li a");

function scrollToSection(element) {

    element.forEach(ele => {

        ele.addEventListener('click', (e) => {

            e.preventDefault();
    
            document.querySelector(e.target.dataset.section).scrollIntoView({
    
                behavior: 'smooth'
    
            });
    
        });
    
    });

}

scrollToSection(allBullets);
scrollToSection(allLinks);

// Array to all new section
// let Arrays = document.querySelectorAll("section");

// Arrays.forEach(ele => {

//     allBullets.forEach(e => {

//         e.dataset.section = ("." + ele.className);

//     });

// });



// class active to element
function handleActive(ev) {
    
    ev.target.parentElement.querySelectorAll(".run").forEach(element => {
        element.classList.remove("run");
    })

        ev.target.classList.add("run");

};

// Bullets options
let BulletsOptions = document.querySelectorAll(".bullets-option span");

let bulletsContainet = document.querySelector(".nav-bullets");

let bulletOP = localStorage.getItem("bullet-option");

let bulletOption = document.querySelectorAll(".bullets-sitting .bullets-option span");

BulletsOptions.forEach(span => {

    span.addEventListener('click', (e) => {

        if (span.dataset.option === 'show') {

            bulletsContainet.style.display = 'block';

            localStorage.setItem("bullet-option", true);
            
        } else {
            
            bulletsContainet.style.display = 'none';

            localStorage.setItem("bullet-option", false);
            
        }

        e.target.parentElement.querySelectorAll("span").forEach(ele => {

            ele.classList.remove("go");

        });

        e.target.classList.add("go");

    });

});

// Set option item in localStorage
if (bulletOP !== null) {

    BulletsOptions.forEach(span => {

        span.classList.remove("go");

    });

    if (bulletOP === 'true') {

        bulletsContainet.style.display = 'block';

        document.querySelector(".Yes").classList.add("go");

    } else {

        bulletsContainet.style.display = 'none';

        document.querySelector(".No").classList.add("go");

    };

};

// Reset options
document.querySelector(".reset").onclick = function() {

    // localStorage.clear();

    localStorage.removeItem("bullet-option");
    
    localStorage.removeItem("random-option");
    
    localStorage.removeItem("color_option");

    window.location.reload();

};

// Toggle open class 
let open = document.querySelector(".header-area .link-container .bar-menu");

let menu = document.querySelector(".header-area .links");

open.onclick = function (e) {

    e.stopPropagation();

    open.classList.toggle("remove");

    menu.classList.toggle("open");

};

menu.onclick = function (e) {

    e.stopPropagation();

}

document.addEventListener('click', (e) => {

    if (e.target !== menu && e.target !== open ) {

        if(menu.classList.contains("open")) {

            menu.classList.remove("open");

            open.classList.add("remove");

        };

    }; 

});

