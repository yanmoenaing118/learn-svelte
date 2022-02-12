<script>
  import Nested from "./Nested.svelte";

  let fname = "";
  let lname = "";
  $: name = [fname, lname];

  $: arr = [];

  let age = "";
  let info = "";

  $: if (age !== "" && !Number.isInteger(parseInt(age))) age = "";

  function handleSubmit(e) {
    e.preventDefault();
    info = `<p style="color: pink">Welcom ${name}</p>`;
  }

  function updateArr() {
    arr = [...arr, 1];
    console.log("arr is ", arr);
  }
</script>

<header>
  <h1>Svelte</h1>
</header>

<main>
  <section>
    <Nested answer={10} />
  </section>
  <section>
    <article>
      <p>
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Debitis maxime
        pariatur impedit. Doloribus maxime ipsam dicta quibusdam provident
        temporibus quisquam, ea beatae veniam voluptate incidunt soluta
        consectetur quod eius ut.
      </p>
    </article>
  </section>

  <section>
    <form action="/" on:submit={handleSubmit} autocomplete="off">
      <div class="form-group">
        <label for="name">First Name: </label>
        <input type="text" name="name" id="fname" bind:value={fname} />
      </div>
      <div class="form-group">
        <label for="name">Last Name: </label>
        <input type="text" name="name" id="lname" bind:value={lname} />
      </div>

      <div class="form-group">
        <label for="age">Age: </label>
        <input type="text" name="age" id="age" bind:value={age} />
      </div>

      <input
        type="submit"
        value="submit"
        disabled={name === "" || age === ""}
      />
    </form>
  </section>

  <section>
    {@html info}
    {name.join(" ")}
  </section>

  <section>
    <button on:click={updateArr}>update arr</button>
    <div>arr length : {arr.length}</div>

    <div>
      <img
        src="http://images.summitmedia-digital.com/preview/images/2021/10/26/peb-nm.jpg"
        alt="Park Eun bin"
      />
    </div>
  </section>
</main>

<style>
  input[type="submit"] {
    border: none;
    background-color: green;
    color: #fff;
    padding: 0.3em 0.5em;
    cursor: pointer;
  }

  input[type="submit"]:disabled {
    background-color: rgb(208, 208, 208);
    color: #fff;
  }

  section {
    margin-bottom: 2em;
    border-bottom: 2px solid green;
  }

  img {
    width: 100%;
    object-fit: cover;
  }
</style>
