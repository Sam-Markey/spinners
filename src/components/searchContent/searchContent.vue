<template>
  <input type="text" v-model="searchText" @keyup="searchForUsers" />
  <div class="search-user-container" v-for="user in searchRes" :key="user.id">
    <img :src="user.profilePicture" alt="user profile picture" />
    <div>
      <h1>{{ user.displayName }}</h1>
      <h3>@{{ user.handle }}</h3>
      <span>{{ user.id }}</span>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, type Ref } from "vue";
import { matchSorter } from "match-sorter";
interface userSearch {
  id: number;
  displayName: string;
  handle: string;
  profilePicture: string;
}
const searchText = ref("");
const searchFeed: userSearch[] = [
  {
    id: 6,
    displayName: "Sam Markey",
    handle: "ori",
    profilePicture:
      "https://images.pexels.com/photos/466685/pexels-photo-466685.jpeg?auto=compress&cs=tinysrgb&w=700",
  },
  {
    id: 4,
    displayName: "john Smith",
    handle: "john",
    profilePicture:
      "https://images.pexels.com/photos/466685/pexels-photo-466685.jpeg?auto=compress&cs=tinysrgb&w=700",
  },
  {
    id: 1,
    displayName: "Abra Con",
    handle: "Abraa",
    profilePicture:
      "https://images.pexels.com/photos/466685/pexels-photo-466685.jpeg?auto=compress&cs=tinysrgb&w=700",
  },
  {
    id: 5,
    displayName: "Pika Chu",
    handle: "Pikachu",
    profilePicture:
      "https://images.pexels.com/photos/466685/pexels-photo-466685.jpeg?auto=compress&cs=tinysrgb&w=700",
  },
  {
    id: 2,
    displayName: "bori Johnson",
    handle: "BorisJohnson",
    profilePicture:
      "https://images.pexels.com/photos/466685/pexels-photo-466685.jpeg?auto=compress&cs=tinysrgb&w=700",
  },
  {
    id: 8,
    displayName: "boriz yohnson",
    handle: "BzrisJohnson",
    profilePicture:
      "https://images.pexels.com/photos/466685/pexels-photo-466685.jpeg?auto=compress&cs=tinysrgb&w=700",
  },
  {
    id: 9,
    displayName: "boris zon",
    handle: "BozisJohnson",
    profilePicture:
      "https://images.pexels.com/photos/466685/pexels-photo-466685.jpeg?auto=compress&cs=tinysrgb&w=700",
  },
  {
    id: 3,
    displayName: "BORI Johnson",
    handle: "BorisZen",
    profilePicture:
      "https://images.pexels.com/photos/466685/pexels-photo-466685.jpeg?auto=compress&cs=tinysrgb&w=700",
  },
];
const searchRes: Ref<userSearch[]> = ref([]);
function searchForUsers(): void {
  searchRes.value = sortSearchFeed(searchFeed, searchText.value);
}
function sortSearchFeed(
  searchFeed: userSearch[],
  searchWord: string
): userSearch[] {
  // return sortByDisplayName(sortByHandle(searchFeed));

  return matchSorter(searchFeed, searchWord, {
    keys: ["displayName", "handle"],
  });
}

// function searchForExactDisplayNameMatch() {

// }
// function sortByDisplayName(searchFeed: userSearch[]): userSearch[] {
//   return searchFeed.sort((current, next) =>
//     current.displayName.toLocaleLowerCase() <
//     next.displayName.toLocaleLowerCase()
//       ? -1
//       : 1
//   );
// }
// function sortByHandle(searchFeed: userSearch[]): userSearch[] {
//   return searchFeed.sort((current, next) =>
//     current.handle.toLocaleLowerCase() < next.handle.toLocaleLowerCase()
//       ? -1
//       : 1
//   );
// }
</script>

<style scoped lang="scss">
.search-user-container {
  display: flex;

  flex-shrink: 0;
  padding: 1rem;
  gap: 20px;
  background-color: lightslategray;

  img {
    border-radius: 50%;
    width: 70px;
    height: 70px;
  }
}
</style>
