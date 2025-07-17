<script>
      import ImageCard from "./lib/ImageCard.svelte";


  let name = "Helen Ma"; // Change this to your name
  let favoriteNumber = 9; // Change this to your favorite number
  let bio = "Greetings! My name is Helen, I'm 20 years old, from Vancouver, BC, and currently a rising senior at the University of British Columbia studying business and computer science. I'm hoping to go into project management after I graduate but very much still exploring what it is I want to do. In my free time, I'm trying new hobbies, spending time in nature,  and purchasing cute stationary I will most likely never use!";
  let hobbies = ["Hiking", "Volunteering", "Kpop"]; // List some hobbies
  
  let cardData = [
    {
      image:
        "IMG_3953.jpg",
      title: "Hiking",
      description:
        "Very blessed to live in the Pacific Northwest where there are so many beautiful trails and parks!! I feel most at peace in the midst of very tall trees <3.",
      imgAlt: "Person posing with one leg up and both hands up, looking happy, on a trail in a sunny forest",
      imgDesc: "Me on a trail in so-called Bowen Island, BC."
    },
    {
      image: "IMG_5157.jpeg",
      title: "Volunteering",
      description: "As an introvert that also craves human connection, volunteering is something I love because it gets me out of my bubble, gives me a better understanding of my local community, and is always a chance to learn new things!",
      imgAlt: "Group of 6 people standing in a cafe with a chalkboard menu behind them that says Sprouts ",
      imgDesc: "Sprouts Cafe, a food security initiative at UBC"

    },
    {
      image: "IMG_1048.jpg",
      title: "K-pop",
      description:"I was a <strong>big</strong> K-pop fan throughout high school and ran 4 different fan accounts at one point (although none very successful and all very embarrassing to look back on haha). My favourite groups/artists include Seventeen, Twice, Pristin, New Jeans, and IU!",
     imgAlt: "Photo of a stage at a stadium, two screens on the side read Seventeen World Tour: Be The Sun",
      imgDesc: "Seventeen's tour in Vancouver in August 2022!"
    },
  ];

  function typewriter(node, { speed = 1 }) {
	const valid = node.childNodes.length === 1 && node.childNodes[0].nodeType === Node.TEXT_NODE;

	if (!valid) {
		throw new Error(`This transition only works on elements with a single text node child`);
	}

	const text = node.textContent;
	const duration = text.length / (speed * 0.01);

	return {
		duration,
		tick: (t) => {
			const i = Math.trunc(text.length * t);
			node.textContent = text.slice(0, i);
		}
	};
} 

</script>

<style>

  :global(body) {
    background-image: url('background.png');
  }

  h1 {
    color: #e97f92;
    font-family: Arial, sans-serif;
    display: center;
  }
  .container {
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
    text-align: center;
  }
  .hobbies {
    display: flex;
    justify-content: center;
    gap: 15px;
    flex-wrap: wrap;
  }
  .hobby {
    background-color: #667a59;
    color: white;
    padding: 10px 15px;
    border-radius: 5px;
  }

  .profile {
    width: 300px;
    height: 300px;
    object-fit: cover;
}

.card-container {
  display: flex;
}


</style>

<div class="bg">
  <div class="container">
    <h1 transition:typewriter>About Me!</h1>
    <p>Hello, my name is <strong>{name}</strong>!</p>
    <p>My favorite number is <strong>{favoriteNumber}</strong>.</p>
    <p>{bio}</p>
    <img class='profile' src='./src/photos/me.JPG' alt='girl wearing blue shirt sitting on grass and holding up a peace sign'>

    <h2>My Hobbies</h2>
    <div class="hobbies">
      {#each hobbies as hobby}
        <div class="hobby">{hobby}</div>
      {/each}
    </div>
  </div>

    <h2>Some of My Favorite Things</h2>
    <div class="card-container">
      {#each cardData as { image, title, description, imgAlt, imgDesc}}
        <ImageCard {image} {title} {description} {imgAlt} {imgDesc} />
      {/each}
    </div>

  </div>