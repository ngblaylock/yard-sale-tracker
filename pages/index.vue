<template>
  <div>
    <div class="jumbotron bg-dark text-white rounded-0 px-0">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-sm-6">
            <h1>Group Sale Tracker</h1>
            <p class="h4">
              Track sales easily with Group Sale Tracker, a free and easy to use
              app.
            </p>
            <hr style="border-color: white;" />
            <p>
              Use categories to separate out sales and let the app do all the
              tricky calculations for you. Whether you are doing a combined yard
              sale, bake sale, concession stand or anything else, Group Sale
              Tracker can improve your sales tracking.
            </p>
            <p>
              <nuxt-link class="btn btn-light" to="/new-sale"
                >Start a New Group Sale</nuxt-link
              >
              <nuxt-link v-if="saleName" class="btn btn-outline-light" to="/app"
                >Continue {{ saleName }}</nuxt-link
              >
            </p>
          </div>
          <div class="col-sm-6">
            <img
              src="~/assets/computer.png"
              class="img-fluid"
              alt="Computer Screen"
            />
          </div>
        </div>
      </div>
    </div>
    <div class="container">
      <div class="row pt-3">
        <div class="col-sm-12">
          <h2 class="h1 text-center">Features</h2>
        </div>
      </div>
      <div class="row align-items-center my-5">
        <div class="col-sm-6">
          <h2>Categorize Your Sales</h2>
          <p>
            Whether you need 1 category, or 100, add as many categories as you
            need for your sale. Common uses for this could be to categorize by
            family names, individuals, item type, or anything else you can think
            of. Cagegories allow you to customize a name and color for any of
            your needs. Group Sale Tracker totals each category for you, and
            lets you how many items were sold.
          </p>
          <p class="alert alert-secondary">
            <strong>Tip:</strong> Consider buying some colored stickers and
            writing the price on them for easy processing at the checkout.
          </p>
        </div>
        <div class="col-sm-4 offset-sm-1">
          <img
            src="~/assets/stickers.png"
            class="img-fluid"
            alt="Sticker Example"
          />
        </div>
      </div>
      <div class="row align-items-center my-5">
        <div class="col-sm-4 offset-sm-1">
          <img src="~/assets/browser-storage.png" class="img-fluid" alt="" />
        </div>
        <div class="col-sm-6 offset-sm-1">
          <h2>In Browser Data Storage</h2>
          <p>
            Group Sale Tracker saves all data to your browser, not on any server
            or cloud platform. This improves privacy by not needing any user
            sign in, integration with a database, and your sales data is never
            sent to anyone else for any reason. Data saved in your browser will
            persist even in the event of needing to restart your computer or by
            closing your browser. Simply open up the same browser on the same
            computer to pick up right where you left off.
          </p>
        </div>
      </div>
      <div class="row align-items-center my-5">
        <div class="col-sm-6">
          <h2>Download and Upload Data</h2>
          <p>
            Do you have a sale that you want to download data for your records?
            What about sharing data with others in your group? No problem. With
            Group Sale Tracker you can download your data to a JSON file, and
            upload it anytime to any modern browser to either check past sales,
            or simply continue right where you left off. You can also take
            advantage of our print-friendly pages to store the information in a
            physical location.
          </p>
        </div>
        <div class="col-sm-4 offset-sm-1">
          <img
            src="~/assets/json.png"
            class="img-fluid"
            alt="Download and Upload Example"
          />
        </div>
      </div>
      <div class="row my-5">
        <div class="col-sm-4">
          <img
            src="https://nathanblaylock.com/img/blaylock-nathan-square.jpg"
            class="rounded-circle img-fluid"
            alt="Nathan's Profile Picture"
          />
        </div>
        <div class="col-sm-8">
          <h2>Free Forever, For Everyone</h2>
          <p>
            That's right. Free, Free, Free. Why is this free? This app is
            designed, developed, and maintained by me,
            <a href="#">*Nathan Blaylock</a>. This app was a fun concept I
            thought of, and wanted to improve my web development skills. So you
            can say that I developed this for fun, hoping that it could help
            someone, somewhere. Because this app uses data stored on your
            machine instead of a database, it doesn't cost me a penny. I have
            however spent many early mornings working on this project.
          </p>
          <p>
            I welcome any <a href="#">*feedback</a> from anyone who has a
            concern or a great idea. Updates may not be very frequent, however,
            I will be sure to prioritize any updates based on the feedback
            recieved.
          </p>
          <p>
            If you find this app helpful for your sale, please consider
            <a href="#">*donating</a> a small amount to my ice cream fund, and
            PLEASE let me know what you used this app for.
          </p>
        </div>
      </div>
    </div>
    <div class="bg-dark text-white p-3 text-center">
      <div class="container">
        <h2 class="mb-4">App Development Tools</h2>
        <div class="d-flex align-items-end justify-content-around">
          <div>
            <img
              src="~/assets/nuxt-white.svg"
              class="tool-logos py-2"
              alt="Nuxt Logo"
            />
            <p>
              Build with Nuxt.js
            </p>
          </div>
          <div>
            <img
              src="~/assets/bootstrap-logo.png"
              class="tool-logos"
              alt="Bootstrap Logo"
            />
            <p>
              Uses Bootstrap 4
            </p>
          </div>
          <div>
            <img
              src="~/assets/font-awesome.png"
              class="tool-logos smaller"
              alt="Font Awesome Logo"
            />
            <p>
              Icons by Font Awesome
            </p>
          </div>
          <div>
            <img
              src="~/assets/Octocat.png"
              class="tool-logos mb-1"
              alt="GitHub Logo"
            />
            <p>Hosted on GitHub Pages</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      saleName: ''
    }
  },
  mounted: function() {
    if (localStorage.saleName) {
      this.saleName = JSON.parse(localStorage.getItem('saleName'))
    }
  }
}
</script>

<style lang="scss" scoped>
.tool-logos {
  max-width: 5em;
  &.smaller {
    max-width: 4.2em;
    padding: 5px;
  }
}
</style>
