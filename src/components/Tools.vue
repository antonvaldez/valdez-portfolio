<template>
  <div class="container mt-5" id="tools">
    <h2>Tools and Technology</h2>
    <div class="row my-5 justify-content-center">
      <div class="col-md-8">
        <div class="accordion my-5" id="accordionExample">
          <div class="accordion-item">
            <h2 class="accordion-header">
              <button class="accordion-button" type="button" data-bs-toggle="collapse" data-bs-target="#collapseOne" aria-expanded="true" aria-controls="collapseOne">
                Front-End
              </button>
            </h2>
            <div id="collapseOne" class="accordion-collapse collapse show" data-bs-parent="#accordionExample">
              <div class="accordion-body">
                <img src="/images/html.png">
                <img src="/images/css.png">
                <img src="/images/bootstrap.jpg">
                <img src="/images/js.webp">
              </div>
            </div>
          </div>
          <div class="accordion-item">
            <h2 class="accordion-header">
              <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseTwo" aria-expanded="false" aria-controls="collapseTwo">
                MEVN
              </button>
            </h2>
            <div id="collapseTwo" class="accordion-collapse collapse" data-bs-parent="#accordionExample">
              <div class="accordion-body">
                <img src="/images/mongo.jpg">
                <img src="/images/express.png">
                <img src="/images/vue.webp">
                <img src="/images/node.png">
              </div>
            </div>
          </div>
          <div class="accordion-item">
            <h2 class="accordion-header">
              <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseThree" aria-expanded="false" aria-controls="collapseThree">
                Other Tools
              </button>
            </h2>
            <div id="collapseThree" class="accordion-collapse collapse" data-bs-parent="#accordionExample">
              <div class="accordion-body">
                <img src="/images/git.webp">
                <img src="/images/postman.webp">
                <img src="/images/sublime.png">
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
