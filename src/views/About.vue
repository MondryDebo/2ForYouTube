<template>
  <div class="about">
    <div class="aboutWrapper">
      <div class="innerWrapper">
        <div class="me">
          <img class="avatar" src="https://avatars.githubusercontent.com/u/84008218?v=4" alt="avatar">
          <div class="name">Tymon Dębicki</div>
          <p>
            Hey, I'm Tymon. I'm from Poland and I'm interested in programming languages 
            ​​such as HTML and JavaScript. For now, I'm learning the "Vue" JavaScript framework.
          </p>
        </div>
        <hr>
        <div class="issues">
          <p>
            Did you found any issues? Report it to me by email 
            <a href="mailto:tymondebicki6@gmail.com">tymondebicki6@gmail.com</a>.
            Thanks!
          </p>
        </div>
        <hr>
        <div class="support">
          <p>
            If you like what I'm doing? I invite you to tip me! Here is my 
            <a href="https://paypal.me/MondryDebo" target="_blank">Paypal</a>
          </p>
        </div>
        <div class="socials-container">
          <a class="socials github" href="https://github.com/MondryDebo"><ion-icon name="logo-github"></ion-icon></a>
          <a class="socials youtube" href="https://www.youtube.com/channel/UCIPkeJj98-pOPTclYaIFx3w"><ion-icon name="logo-youtube"></ion-icon></a>
          <a class="socials twitter" href="https://twitter.com/MondryD3bo"><ion-icon name="logo-twitter"></ion-icon></a>
          <a class="socials instagram" href="https://www.instagram.com/mondrydebo/"><ion-icon name="logo-instagram"></ion-icon></a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'About',
}
</script>

<style lang="scss" scoped>
  .about {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .aboutWrapper {
    margin: 50px;
    border: 1px solid rgba(0, 0, 0, 0.1);
    width: 75%;
    height: auto;
    background: white;
    border-radius: 15px;
    box-shadow: 0 30px 30px -10px rgba(0, 0, 0, .3);
    padding: 50px;
  }

  .innerWrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  .me {
    width: 500px;

    .avatar {
      height: 125px;
      width: 125px;
      border-radius: 50%;
    }

    .name {
      font-weight: 600;
    }
  }

  .issues {
    width: 500px;
  }

  .socials-container {
    margin-top: 15px;
  }

  .socials {
    margin: 0.25em;
    font-size: 1.75em;
    color: rgb(100, 100, 100);
  }

  p {
    a {
      &:hover {
        text-decoration: underline;
      }
    }
  }

  hr {
    margin: 15px;
    width: 600px;
  }
</style>
