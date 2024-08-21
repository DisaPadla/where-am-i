<script lang="ts">
  import { onMount } from 'svelte';
  import { tweened } from 'svelte/motion';

  const phrase = 'あなた一人じゃありません';
  const fullName = 'Denys Skolzin';
	const randomSymbols = [...phrase.split(''), ...fullName.split('')]; 
  let randomPhrase = '';
  let duration = 2000;
	let playing = false;
	let width;
  const time = tweened(0);
	const value = tweened(1000);

  const getRandomText = () => {
    const symbols = [];
    for (let i = 0; i < fullName.length; i++) {
      const randomIndex = Math.floor(Math.random() * randomSymbols.length);
      symbols.push(randomSymbols[randomIndex]);
    }
    return symbols.join('');
  }

  const switchFullName = () => {
    if (randomPhrase === fullName) {
      randomPhrase = phrase;
    } else {
      randomPhrase = fullName;
    }
  }

  onMount(() => {
    // setInterval(() => {
    //   randomPhrase = getRandomText();
    // }, 300);
    randomPhrase = getRandomText();
  });
</script>

<div class="container">
	<header>
    <span>
      <h4 class='text'>About:</h4>&nbsp
      <span class='glitch-wrapper'>
        <h4 class='text glitch' on:click={switchFullName}>{randomPhrase}</h4>
      </span>
    </span>
		<a class='text' target="_blank" href="https://scp-wiki.wikidot.com/scp-507">#507</a>
	</header>
	<main>
		<video autoplay loop muted width="200" height="200" class="avatar" src="./src/assets/avatar.mp4">
			A man moving his hands away from his forehead sideways, in a mind-explosion gesture. An overlaid animation enforces the explosion character.
		</video>
	</main>
	<footer>
		<span class='text'>Inspired by</span>&nbsp 
		<span class='text scp'>███ ██████████</span>
	</footer>
</div>

<style>
	.container {
		display: grid;
		grid-template-areas:
			'header header header header header header'
			'main main main main right right'
			'footer footer footer footer footer footer';
		gap: 1rem;
		display: flex;
		flex-direction: column;
		height: 100vh;
		width: 100vw;
		padding: 2rem;
		background: linear-gradient(180deg, rgba(35,33,31,1) 58%, rgba(64,64,119,1) 97%, rgba(140,84,168,1) 100%);
	}

	header {
		grid-area: header;
		display: flex;
		justify-content: space-between;
		width: 100%;
		padding: 1rem 0;
		margin-bottom: 1rem;
		border-bottom: 2px solid #6d60b2;
	}

	main {
		grid-area: main;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	footer {
		grid-area: footer;
		display: flex;
		justify-content: center;
		width: 100%;
		margin: 0 auto;
	}

	.scp {
		color: black;
	}

	.avatar {
		border: 1px solid #6d60b2;
	}

	.text {
		margin: 0;
		background-image: linear-gradient(180deg, #f1faff, #925daf);
		background-size: 100%;
  	background-repeat: repeat;
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent; 
		-moz-background-clip: text;
		-moz-text-fill-color: transparent;
	}

  .glitch-wrapper {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    position: relative;
    text-align: center;
    background-color: #222222;
    overflow: auto;
  }

  .glitch {
    position: relative;
    margin: auto;
    line-height: 1.2;
    color: #FFFFFF;
    letter-spacing: 5px;
    animation: 4s ease-in-out infinite alternate shift;
    z-index: 1;
  }

  .glitch:after, .glitch:before {
    content: attr(data-glitch);
    position: absolute;
    top: 0;
    width: 100%;
    color: #fff;
    background-color: #222;
    overflow: hidden;
    clip: rect(0,900px,0,0);
  }

  .glitch:before {
    left: -2px;
    animation: 3s linear infinite alternate-reverse noise-before;
  }

  .glitch:after {
    left: 2px;
    animation: 2s linear infinite alternate-reverse noise-after;
  }

  @keyframes noise-before {
    0% {
        clip: rect(61px,9999px,52px,0);
    }
    5% {
        clip: rect(33px,9999px,144px,0);
    }
    10% {
        clip: rect(121px,9999px,115px,0);
    }
    15% {
        clip: rect(144px,9999px,162px,0);
    }
    20% {
        clip: rect(62px,9999px,180px,0);
    }
    25% {
        clip: rect(34px,9999px,42px,0);
    }
    30% {
        clip: rect(147px,9999px,179px,0);
    }
    35% {
        clip: rect(99px,9999px,63px,0);
    }
    40% {
        clip: rect(188px,9999px,122px,0);
    }
    45% {
        clip: rect(154px,9999px,14px,0);
    }
    50% {
        clip: rect(63px,9999px,37px,0);
    }
    55% {
        clip: rect(161px,9999px,147px,0);
    }
    60% {
        clip: rect(109px,9999px,175px,0);
    }
    65% {
        clip: rect(157px,9999px,88px,0);
    }
    70% {
        clip: rect(173px,9999px,131px,0);
    }
    75% {
        clip: rect(62px,9999px,70px,0);
    }
    80% {
        clip: rect(24px,9999px,153px,0);
    }
    85% {
        clip: rect(138px,9999px,40px,0);
    }
    90% {
        clip: rect(79px,9999px,136px,0);
    }
    95% {
        clip: rect(25px,9999px,34px,0);
    }
    100% {
        clip: rect(173px,9999px,166px,0);
    }
  }

  @keyframes noise-after {
      0% {
          clip: rect(26px,9999px,33px,0);
      }

      5% {
          clip: rect(140px,9999px,198px,0);
      }

      10% {
          clip: rect(184px,9999px,89px,0);
      }

      15% {
          clip: rect(121px,9999px,6px,0);
      }

      20% {
          clip: rect(181px,9999px,99px,0);
      }

      25% {
          clip: rect(154px,9999px,133px,0);
      }

      30% {
          clip: rect(134px,9999px,169px,0);
      }

      35% {
          clip: rect(26px,9999px,187px,0);
      }

      40% {
          clip: rect(147px,9999px,137px,0);
      }

      45% {
          clip: rect(31px,9999px,52px,0);
      }

      50% {
          clip: rect(191px,9999px,109px,0);
      }

      55% {
          clip: rect(74px,9999px,54px,0);
      }

      60% {
          clip: rect(145px,9999px,75px,0);
      }

      65% {
          clip: rect(153px,9999px,198px,0);
      }

      70% {
          clip: rect(99px,9999px,136px,0);
      }

      75% {
          clip: rect(118px,9999px,192px,0);
      }

      80% {
          clip: rect(1px,9999px,83px,0);
      }

      85% {
          clip: rect(145px,9999px,98px,0);
      }

      90% {
          clip: rect(121px,9999px,154px,0);
      }

      95% {
          clip: rect(156px,9999px,44px,0);
      }

      100% {
          clip: rect(67px,9999px,122px,0);
      }
}
</style>
