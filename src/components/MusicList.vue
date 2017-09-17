<template>
	<div id="music-list" class="col-sm-12">
		<div class="row">
			<SearchBar @dataMusic="musicList"/>
			<div class="col-sm-4" v-for="music in data">
				<div class="card">
					<img class="card-img-top" v-bind:src="music.artwork_url" alt="">
					<div class="play-track">
						<div class="play-track-inner" @click="musicPlay(music.stream_url)">
							<span v-if="playingUrl !== music.stream_url">&#9654;</span>
							<span v-if="playingUrl === music.stream_url">||</span>
						</div>
					</div>
				</div>
			</div>
	   </div>
	</div>
</template>

<script>

import SearchBar from './SearchBar'

export default {
	name: 'music-list',
	data: function() {
		return {
			data: [],
			playingUrl: '',
			playing: false,
			audio: null
		}
	},
	components: { SearchBar },
	template: '<SearchBar />',
	methods: {
		musicList: function(response) {
			console.log(response);
			(response.success !== false) ? this.data = response : this.data = [];
		},
		musicPlay: function(url) {
			const audio = new Audio(url);

			if(this.playing === false) {

				audio.play();

				this.playingUrl = url;
				this.playing = true;
				this.audio = audio;

			}else{

				if(this.playingUrl === url) {

					this.audio.pause();
					this.playing = false;
				}
				else{
					this.audio.pause();
					audio.play();

					this.playingUrl = url,
					this.playing = true;
					this.audio = audio;
				}
			}
		}
	}
}

</script>