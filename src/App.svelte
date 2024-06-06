<script lang="ts">
  import conan from './assets/defaultImage.jpeg';
  import crushTheEnemies from './assets/crushTheEnemies.jpg';
  import drivenBeforeYou from './assets/drivenBeforeYou.jpg';
  import lamentationOfWomen from './assets/lamentationOfWomen.jpg';
type Item = {
  id: number,
  text: string,
  imageURL?: string
}

let defaultImageURL = conan;
let activeImage = defaultImageURL;

let items: Item[] = [
  {
    id: 1,
    text: "To crush your enemies,",
    imageURL: crushTheEnemies,
  },
  {
    id: 2,
    text: "see them driven before you,",
    imageURL: drivenBeforeYou,
  },
  {
    id: 3,
    text: "and to hear the lamenetation of their women!",
    imageURL: lamentationOfWomen,
  }
]

function changeBackgroundImage(item: Item){
  activeImage = item.imageURL || defaultImageURL;
}

function resetBackgroundImage() {
  activeImage = defaultImageURL;
}

</script>

<!-- Tailwind to apply a class to all descendants of an element add [&_*]
    if only first children then [&>*]
    if specific element then [&_p] -->
<main id="menu" class="m-0 h-screen flex gap-4 items-center">
  <div id="items" class="flex flex-col gap-5 [&_*]:hover:opacity-25 z-10" on:mouseleave={() => resetBackgroundImage()}>
    {#each items as item}
        <div class="transition ml-36 ease-in-out duration-200 text-6xl hover:!opacity-100 cursor-pointer" on:mouseover={()=> changeBackgroundImage(item)}>{item.text}</div>
    {/each}
  </div>
  <img class="absolute bg-cover bg-center top-0 left-0 z-0 opacity-20 object-cover object-top h-screen w-screen" src={activeImage} alt="Default Image" />
</main>

<!-- https://css-tricks.com/on-object-fit-and-object-position/
  good document describing how the position viewport changes-->