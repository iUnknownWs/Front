<template>
  <form>
    <div className="flex flex-col gap-4">
      <label>
        Draft:
        <input type="checkbox" id="name" name="name" required />
      </label>
      <label>
        Title
        <input type="text" id="name" name="name" required />
      </label>
      <label>
        Description
        <input type="message" id="description" name="description" required />
      </label>
      <label>
        Date
        <input type="date" id="date" name="date" required />
      </label>
      <label>
        CoverSVG
        <input type="file" id="cover" name="cover" required />
      </label>
      <label>
        SocialSVG
        <input type="file" id="social" name="social" required />
      </label>
      <label>
        {{ author }}
        <select name="author" id="author">
          <option v-for="author in authors" value={{ author.id }}> {{ author.name }} </option>
        </select>
      </label>
      <label>
        Category
        <select name="category" id="category">
          <option v-for="category in categories" value={{ category.id }}> {{ category.name }} </option>
          <option value='1'> Hola </option>
        </select>
      </label>
      <label>
        Tags:
        <input type="checkbox" id="tag" name="tag" required />
      </label>
    </div>
    <button>Send</button>
  </form>
</template>

<script>
export default {
  name: 'Form',
  data() {
    return {
      author: 'Willders Carvajal',
      authors: [],
      categories: [],
    }
  },
  methods: {
    async getAuthors() {
      let response = await fetch('http://localhost:8000/api/author/')
      let data = await response.json()
      console.log(data)
      this.author = "culo peluo"
      this.authors = data
    },
    async getCategories() {
      let response = await fetch('http://localhost:8000/api/category/')
      let data = await response.json()
      console.log(data)
      this.categories = data
    }
  },
  created() {
    this.getAuthors()
    this.getCategories()
  }
}
</script>
