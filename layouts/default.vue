<script setup>

const path = () => useRoute().path

const items = [
  { page: 'Home', path: '/' },
  { page: 'People', path: '/people' },
  { page: 'Planets', path: '/planets' },
  { page: 'Species', path: '/species' },
  { page: 'Starships', path: '/starships' },
  { page: 'Vehicles', path: '/vehicles' },
]

</script>


<template>
  <div>
    <header>
      <nav>
        <span>
          <NuxtLink to="/">
            STAR WARS
          </NuxtLink>
        </span>
        <ul>
          <li
            v-for="item in  items"
            :key="item.page"
          >
            <NuxtLink
              :to="item.path"
              :class="{ active: path() === item.path }"
            >
              {{ item.page }}
            </NuxtLink>
          </li>
        </ul>
      </nav>
    </header>
    <slot />
  </div>
</template>


<style scoped>
nav {
  height: 80px;
  font-size: 24px;
  background-color: gray;
  display: flex;
  justify-content: space-between;
}

span {
  margin: auto 30px;
  color: goldenrod;
  font-weight: bold;
  font-size: 200%;
}

ul {
  display: flex;
  align-self: center;
  position: absolute;
  right: 0;
}

ul li {
  margin-right: 30px;
}

ul li:hover {
  color: goldenrod;
}

.active {
  color: goldenrod;
  text-decoration: underline;
}
</style>
