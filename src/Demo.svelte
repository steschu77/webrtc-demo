<script>
    import Participant from './Participant.svelte';
    let events = [];
    const addEvent = ({ detail }) => {
        events = [...events, detail];
    };
</script>

<style>
    section {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
    }

    div {
        padding: 1em;
        border: 1px solid #aaa;
        border-radius: 2px;
        box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.1);
        margin: 0 0 1em 0;
    }

    code {color: red;}
</style>

<div>
    <nav />
    <section>
        <Participant name="alice" isCaller="true" recipient="bob" on:event={addEvent} />
        <Participant name="bob" isReceiver="true" recipient="alice" on:event={addEvent} />
        <ol>
            {#each events.filter(e => e.event) as { name, event }}
                <li> {name}: {event} </li>
            {/each}
        </ol>
        <em>please open <code> chrome://webrtc-internals </code> </em>
    </section>
</div>
