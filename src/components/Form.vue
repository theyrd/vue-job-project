<template>
  <div class="form-div">
    <form
      action="https://webhook.site/6352ff2a-f473-455f-ad44-d6c6f83d8422"
      class="add-form"
      method="post"
    >
      <div class="form-control">
        <input
          type="text"
          v-model="name"
          name="name"
          id="name"
          placeholder="Enter your name"
          style="width: 25vw"
          required
        />
      </div>

      <div class="form-control">
        <input
          type="email"
          v-model="email"
          name="email"
          id="email"
          placeholder="Enter your email"
          style="width: 25vw"
          required
        />
      </div>

      <div class="form-control">
        <input
          type="number"
          v-model="phone_number"
          name="phone-number"
          id="phone-number"
          placeholder="Enter your number"
          style="width: 20vw"
          required
        />
      </div>

      <div class="form-control">
        <input class="btn" type="submit" name="submit" value="Submit" />
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "Form",
};
</script>

<style>
.form-div {
  width: 30vw;
  display: inline-block;
}

.btn {
  width: 200px;
  background-color: yellowgreen;
}

.form-control {
  padding: 5px;
  margin: 5px;
  border: 2px solid black;
}
</style>
