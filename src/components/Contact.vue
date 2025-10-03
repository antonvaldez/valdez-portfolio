<template>
<div class="container" id="contact">
    <h2>Contact me!</h2>
    <div class="row my-5 justify-content-center">
      <div class="col-md-6">
        <form action="https://google.com">
          <input type="text" name="name" placeholder="First Name, Last Name" class="form-control" required autocomplete>
          <input type="text" name="email"  placeholder="Email" class="form-control mt-1" required autocomplete>
          <textarea rows="5" class="form-control mt-1" placeholder="Enter your message here..."></textarea>
          <div class="d-flex justify-content-center gap-2 mt-3">
            <a href="https://www.linkedin.com/" target="_blank">
              <img src="https://cdn-icons-png.flaticon.com/256/174/174857.png">
            </a>
            <a href="https://github.com" target="_blank">
              <img src="https://cdn-icons-png.flaticon.com/256/25/25231.png">
            </a>
            <a href="https://about.gitlab.com" target="_blank">
              <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQTMU0Ge8750e3MFRuLtBi_nu8MlsLnuCT5UQ&s">
            </a>
            <button type="submit" class="form-button ms-auto">Submit</button>
            <button type="reset" class="form-button">Reset</button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>
