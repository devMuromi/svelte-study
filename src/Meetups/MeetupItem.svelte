<script>
	export let meetup;
</script>

<article>
	<header>
		<h1>{meetup.title}</h1>
		<h3>{meetup.subtitle}</h3>
		<h2>{meetup.address}</h2>
	</header>
	<div class="image">
		<img src={meetup.imageUrl} alt="" />
	</div>
	<div>
		<div class="content">
			<p>{meetup.description}</p>
		</div>
		<footer>
			<a href="mailto:{meetup.email}">Contact</a>
			<button>Show Details</button>
			<button>Favorite</button>
		</footer>
	</div>
</article>

<style>
	article {
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
		border-radius: 5px;
		background: white;
		margin: 1rem;
	}
	header,
	.content,
	.footer {
		padding: 1rem;
	}
	.image {
		width: 100%;
		height: 14rem;
	}
	p {
		font-size: 1.25rem;
		margin: 0;
	}
	div {
		text-align: right;
	}
</style>
