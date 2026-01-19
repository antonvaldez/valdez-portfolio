<template>
  <div class="container" id="landing">
    <div class="row justify-content-center align-items-center my-5">
      <div class="col-lg-3 col-md-4 col-12 d-flex justify-content-center mb-4 mb-md-0">
        <img src="/images/anton.jpg" class="landing-img" alt="Anton">
      </div>
      <div class="col-lg-7 col-md-8 col-12">
        <h1>Manuel Antonio C. Valdez III HELLO</h1>
        <h3>Full Stack Web Developer</h3>
        <p>I’ve always enjoyed solving problems and building things, which eventually led me to discover web development. I started learning on my own, and the more I explored coding, the more I realized I wanted to do this full time. Coming from a different field, I decided to fully shift gears and join a bootcamp to focus on full stack development. Now, I'm all in on becoming a developer and excited to keep learning and building.</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.landing-img {
  width: 100%;
  max-width: 250px;
  height: auto;
  object-fit: cover;
  border-radius: 10px;
}

@media (max-width: 768px) {
  .landing-img {
    max-width: 180px;
  }
}
</style>
