<script lang="ts">
	import { onMount } from 'svelte';
	import { base } from '$app/paths';
	import '../app.css';

    let timerElement: HTMLElement;
    onMount(() => {

        const raceDate = new Date('2025-11-09T09:00:00').getTime();

        const updateTimer = () => {
            const now = new Date().getTime();
            const distance = raceDate - now;

            if (distance < 0) {
                if (timerElement) {
                    timerElement.innerHTML = "The race is over! Who won?";
                }
                clearInterval(interval);
                return;
            }

            const days = Math.floor(distance / (1000 * 60 * 60 * 24));
            const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((distance % (1000 * 60)) / 1000);

            if (timerElement) {
                timerElement.innerHTML = `${days}d ${hours}h ${minutes}m ${seconds}s`;
            }
        };

        const interval = setInterval(updateTimer, 1000);
        updateTimer(); // Initial call to display timer immediately

        return () => {
            clearInterval(interval);
        };
    });
</script>

<div class="hero-section">
    <div class="animated-bg"></div>
    <div class="container">
        <div id="countdown" class="countdown-section">
            <h3 class="countdown-title">COUNTDOWN TO DESTRUCTION</h3>
            <div id="timer" class="timer" bind:this={timerElement}></div>
            <div class="countdown-subtext">Time until David realizes he's not as fast as he thinks</div>
        </div>

        <div class="challenge-section">
            <h2 class="section-title">THE CHALLENGE</h2>
            <div class="challenge-box">
                <p class="backstory">
                    It all started during a volleyball game at Rivi. David suggested a run at Sunset Cliffs, and when I mentioned his pace might be faster, he hit me with a casual, "You should step it up."
                    <br /><br />
                    I took that personally. After carrying him in volleyball tournaments for two years, it's
                    time to drop the dead weight. On November 9, 2025, we settle this. Not with words,
                    but with sweat, grit, and a definitive finish line. It's time to prove that, as
                    Aristotle taught, excellence is not an act, but a habit. The exact bet is TBD, but
                    his pride is on the line.
                </p>
            </div>
        </div>

        <div class="weaknesses-section">
            <h2 class="section-title">DAVID'S DOCUMENTED WEAKNESSES</h2>
            <div class="weaknesses-grid">
                <div class="weakness-card">
                    <div class="weakness-icon"></div>
                    <p>Suffers from a crippling case of party FOMO</p>
                </div>
                <div class="weakness-card">
                    <div class="weakness-icon"></div>
                    <p>An aficionado of beer, which he considers an essential part of his day</p>
                </div>
                <div class="weakness-card">
                    <div class="weakness-icon"></div>
                    <p>Thinks "endurance training" is surviving a week at Burning Man</p>
                </div>
                <div class="weakness-card">
                    <div class="weakness-icon"></div>
                    <p>Would rather be in the Canary Islands, feasting like a king</p>
                </div>

            </div>
        </div>
        <div class="cta-section">
            <a href="https://endurancecui.active.com/new/events/93128803/select-race?rcid=97C0EA38-7605-4F1B-9EFF-7B3DF8422E5A&mrrId=3acffec8-0e0b-47de-8f4f-a17138379fb9&_p=056395702252372004&e4q=5ce608c1-a3bf-4031-9449-68c99b5f9ff9&e4p=73e99789-9697-4b07-89c4-8392ef9e057b&e4ts=1754678713&e4c=active&e4e=snawe00000000&e4rt=Safetynet&e4h=961554fa8844a77c4f0f414a87faa23b&error=login_required&state=66862efa-d297-47c4-84fb-7851f948e810" class="register-button" target="_blank">
                <span class="button-text">REGISTER FOR THE SHOWDOWN</span>
                <span class="button-subtext">David, your time has come</span>
            </a>
        </div>

        <div class="poll-section">
            <h2 class="section-title">WHO WILL WIN?</h2>
            <img src="{base}/david&I.jpeg" alt="David and I" class="poll-image" />
            <iframe src="https://strawpoll.com/embed/GeZARPe6kyV" title="Who will win?" style="width: 100%; max-width: 500px; height: 410px; border: 0;"></iframe>
        </div>
    </div>
</div>
