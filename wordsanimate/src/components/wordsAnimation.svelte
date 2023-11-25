<script>
    import Letter from "./letterAnimation.svelte";

    const wordsList = [
        ["M", "U", "H", "A", "M", "M", "A", "D", "", "", ""],
        ["Z", "A", "I", "N", "", "", "", "", "", "", ""],
        ["", "A", "", "N", "S", "A", "R", "I", "", "", ""],
        ["F", "R", "O", "N", "T", "E", "N", "D", "", "", ""],
        ["D", "E", "V", "E", "L", "O", "P", "E", "R", "", ""],
    ];
    let i = 0;
    let currentWord = wordsList[i];
    let wordColor;
    /** unpdates to the next work */
    function changeWorld() {
        if (i < 4) {
            i++;
        } else {
            i = 0;
        }
        currentWord = wordsList[i];
        // console.log('i', i);
        setTimeout(changeWorld, 3000);
        if (i == 0) {
            wordColor = "rgba(255, 80, 118, 1)";
        } else if (i == 1) {
            wordColor = "#DA22FF";
        } else if (i == 2) {
            wordColor = "rgba(28, 123, 255, 1)";
        } else if (i == 3) {
            wordColor = "rgba(50, 171, 171, 1)";
        } else {
            wordColor = "rgba(255, 153, 7, 1)";
        }
    }

    changeWorld();
</script>

<div class="container">
    {#each wordsList[0] as _, index}
        <div class="letter">
            <Letter letter={currentWord[index]} letterColor={wordColor} />
        </div>
    {/each}
</div>

<style>
    .container {
        display: flex;
        width: fit-content;
        height: inherit;
        transition: 1s;
        margin: auto;
    }
    .letter {
        position: relative;
        width: fit-content;
        height: inherit;
    }
</style>
