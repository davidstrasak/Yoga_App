<script lang="ts">
	let videoId = 'o_73FeXw3ZI';
	let featuredVideos = [
		{ id: 'o_73FeXw3ZI', title: 'Start Your Day With This', length: '9.5' },
		{ id: 'PzSVekqNiuA', title: 'Yoga for Beginners', length: '7' },
		{ id: 'hJbRpHZr_d0', title: 'Yoga for anxiety', length: '27' },
		{ id: 'sTANio_2E0Q', title: 'Stretch Yoga', length: '19' },
		{ id: 'GLy2rYHwUqY', title: 'Total Deep Stretch Yoga', length: '45' }
	];

	function changeVideo(id: any) {
		videoId = id;
		window.scrollTo({ top: 0, behavior: 'smooth' });
	}
</script>

<div class="page-container">
	<h1 class="page-title">Yoga Videos</h1>

	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/{videoId}?si=AZesi6gGeYbmyfw3"
			title="YouTube video player"
			frameborder="0"
			allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
			referrerpolicy="strict-origin-when-cross-origin"
			allowfullscreen
		></iframe>
	</div>

	<div class="video-controls">
		<button class="control-btn">
			<svg
				xmlns="http://www.w3.org/2000/svg"
				width="24"
				height="24"
				viewBox="0 0 24 24"
				fill="none"
				stroke="currentColor"
				stroke-width="2"
				stroke-linecap="round"
				stroke-linejoin="round"
			>
				<path d="M19 12H5M12 19l-7-7 7-7" />
			</svg>
			Previous
		</button>
		<button class="control-btn favorite-btn">
			<svg
				xmlns="http://www.w3.org/2000/svg"
				width="24"
				height="24"
				viewBox="0 0 24 24"
				fill="none"
				stroke="currentColor"
				stroke-width="2"
				stroke-linecap="round"
				stroke-linejoin="round"
			>
				<path
					d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"
				/>
			</svg>
			Favorite
		</button>
		<button class="control-btn">
			Next
			<svg
				xmlns="http://www.w3.org/2000/svg"
				width="24"
				height="24"
				viewBox="0 0 24 24"
				fill="none"
				stroke="currentColor"
				stroke-width="2"
				stroke-linecap="round"
				stroke-linejoin="round"
			>
				<path d="M5 12h14M12 5l7 7-7 7" />
			</svg>
		</button>
	</div>

	<section class="video-section">
		<h2>More Videos</h2>
		<div class="video-grid">
			{#each featuredVideos as video}
				<div
					class="video-card"
					class:active={video.id === videoId}
					on:click={() => changeVideo(video.id)}
					on:keydown={(e) => e.key === 'Enter' && changeVideo(video.id)}
					role="button"
					tabindex="0"
					aria-label="Play {video.title}"
				>
					<div class="thumbnail">
						<img
							src="https://i.ytimg.com/vi/{video.id}/mqdefault.jpg"
							alt={video.title}
							loading="lazy"
						/>
						<div class="play-icon">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								width="24"
								height="24"
								viewBox="0 0 24 24"
								fill="currentColor"
							>
								<polygon points="5 3 19 12 5 21 5 3"></polygon>
							</svg>
						</div>
					</div>
					<h3 class="">{video.length}min - {video.title}</h3>
				</div>
			{/each}
		</div>
	</section>
</div>

<style>
	.page-container {
		padding-bottom: 2rem;
	}

	.page-title {
		font-size: 1.8rem;
		margin: 0.5rem 0 1rem;
		color: #333;
	}

	.video-container {
		position: relative;
		padding-bottom: 56.25%; /* 16:9 Aspect Ratio */
		height: 0;
		overflow: hidden;
		border-radius: 12px;
		box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
		background-color: #000;
		margin-bottom: 1rem;
	}

	.video-container iframe {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		border: 0;
	}

	.video-controls {
		display: flex;
		justify-content: space-between;
		margin: 1rem 0 1.5rem;
	}

	.control-btn {
		display: flex;
		align-items: center;
		gap: 0.5rem;
		padding: 0.6rem 1rem;
		border: none;
		background-color: #6b46c1;
		color: white;
		border-radius: 8px;
		font-weight: 500;
		cursor: pointer;
		transition:
			background-color 0.2s,
			transform 0.1s;
	}

	.control-btn:hover {
		background-color: #553c9a;
	}

	.control-btn:active {
		transform: scale(0.98);
	}

	.favorite-btn {
		background-color: #e53e3e;
	}

	.favorite-btn:hover {
		background-color: #c53030;
	}

	.video-section {
		margin-top: 2rem;
	}

	.video-section h2 {
		font-size: 1.4rem;
		margin-bottom: 1rem;
		color: #444;
	}

	.video-grid {
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
		gap: 1rem;
	}

	.video-card {
		background-color: white;
		border-radius: 8px;
		overflow: hidden;
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.06);
		transition:
			transform 0.2s,
			box-shadow 0.2s;
		cursor: pointer;
	}

	.video-card:hover {
		transform: translateY(-2px);
		box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
	}

	.video-card.active {
		border: 2px solid #6b46c1;
	}

	.thumbnail {
		position: relative;
		padding-bottom: 56.25%;
		background-color: #f0f0f0;
	}

	.thumbnail img {
		position: absolute;
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.play-icon {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		background-color: rgba(0, 0, 0, 0.7);
		color: white;
		width: 36px;
		height: 36px;
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.video-card h3 {
		font-size: 0.9rem;
		padding: 0.5rem;
		margin: 0;
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
	}

	@media (min-width: 480px) {
		.video-grid {
			grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
		}
	}
</style>
