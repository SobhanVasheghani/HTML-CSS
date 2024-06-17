<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link href='https://unpkg.com/boxicons@2.1.4/css/boxicons.min.css' rel='stylesheet'>
  <title>Classic Header</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800;900&display=swap');

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    text-decoration: none;
    border: none;
    outline: none;
    scroll-behavior: smooth;
    font-family: 'Poppins', sans-serif;
}

:root{
    --bg-color: #1f242d;
    --second-bg-color: #323946;
    --text-color: #fff;
    --main-color: #0ef;
}

html{
    font-size: 62.5%;
    overflow-x: hidden;
}

body {
    background: var(--bg-color) ;
    color: var(--text-color);
}

.header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    padding: 2rem 9%;
    background: var(--bg-color);
    display: flex;
    justify-content: space-between;
    align-items: center;
    z-index: 100;
}

.header.sticky{
    border-bottom: .1rem solid rgba(0, 0, 0, .2);
    top: 0;
}

.logo{
    font-size: 2.5rem;
    color: var(--text-color);
    font-weight: 600;
    cursor: default;
}

.navbar a{
    font-size: 1.7em;
    color: var(--text-color);
    margin-left: 4rem;
    transition: .3s;
}

.navbar a:hover,
.navbar a.active
{
    color: var(--main-color);
}

#menu-icon{
    font-size: 3.6em;
    color: var(--text-color); 
    display: none;
}

/* =============== Let's Make It Responsive =============== */

/*=============== 1200 ===============*/

@media (max-width: 1200px) {
    html{
        font-size: 55%;
    }
}

/*=============== 991 ===============*/

@media (max-width: 991px) {
    .header{
        padding: 2rem 3%;
    }
}

/*=============== 768 ===============*/

@media (max-width: 768px) {
    #menu-icon{
        display: block;
    }

    .navbar {
        position: absolute;
        top: 100%;
        left: 0;
        width: 100%;
        padding: 1rem 3%;
        background: var(--bg-color);
        border-top: .1rem solid rgba(0, 0, 0, .2);
        box-shadow: 0 .5rem 1rem rgba(0, 0, 0, .2);
        display: none;
    }

    .navbar.active{
        display: block;
    }

    .navbar a{
        display: block;
        font-size: 2rem;
        margin: 3rem 0;
    }
}

/*=============== 450 ===============*/

@media (max-width: 450px){
    html{
        font-size: 50%;
    }
}
  </style>
</head>
<body>

    <!-- header design -->

    <header class="header">
    <a href="#" class="logo">portfolio</a>

    <i class='bx bx-menu' id="menu-icon"></i>

    <nav class="navbar">
        <a href="#home" class="active">Home</a>
        <a href="#about">About</a>
        <a href="#services">Services</a>
        <a href="#portfolio">Portfolio</a>
        <a href="#contact">Contact</a>
    </nav>
    </header>

    <script>
      /*==================== toggle icon navbar ====================*/
      let menuIcon = document.querySelector('#menu-icon');
      let navbar = document.querySelector('.navbar');
      
      menuIcon.onclick = () => {
          menuIcon.classList.toggle('bxs-shield-x');
          navbar.classList.toggle('active'); 
      };
      
      /*==================== scroll sections active link ====================*/
      let sections = document.querySelectorAll('section');
      let navLinks = document.querySelectorAll('header nav a');
      
      window.onscroll = () => {
          sections.forEach(sec => {
              let top =window.scrollY;
              let offset = sec.offsetTop - 150;
              let height = sec.offsetHeight;
              let id = sec.getAttribute('id');
      
              if(top >= offset && top < offset + height) {
                  navLinks.forEach(links => {
                      links.classList.remove('active');
                      document.querySelector('header nav a[href*=' + id +']').classList.add('active');
                  });
              };
          });
          /*=========================== sticky navbar ========================*/
          let header = document.querySelector('header');
      
          header.classList.toggle('sticky', window.scrollY > 100);
      
          /*==================== remove toggle icon and navbar when click navbar link (scroll)====================*/
          menuIcon.classList.remove('bxs-shield-x');
          navbar.classList.remove('active');
      };

    </script>

</body>
</html>
