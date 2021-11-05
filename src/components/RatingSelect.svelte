<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    let RatingData = [];

    [...Array(10).keys()].map((number) =>
        RatingData.push({
            id: `num${number + 1}`,
            value: number + 1,
        })
    );

    let selected = 10;

    const onChange = (e) => {
        selected = e.currentTarget.value;
        dispatch("rating-select", selected);
    };
</script>

<style>
    .rating {
        display: flex;
        align-items: center;
        justify-content: space-around;
        flex-wrap: wrap;
        gap: 3px;
        margin: 30px 0;
    }
    .rating li {
        position: relative;
        background: #f4f4f4;
        width: 50px;
        height: 50px;
        padding: 10px;
        text-align: center;
        border-radius: 50%;
        font-size: 19px;
        border: 1px #eee solid;
        transition: 0.3s;
    }
    .rating li label {
        position: absolute;
        top: 50%;
        left: 50%;
        width: 50px;
        height: 50px;
        padding: 10px;
        border-radius: 50%;
        transform: translate(-50%, -50%);
        cursor: pointer;
    }
    .rating li:hover {
        background: #ff6a95;
        color: #fff;
    }
    /* Make actual radio select invisible */
    [type="radio"] {
        opacity: 0;
    }
    /* Use the sibling select */
    [type="radio"]:checked ~ label {
        background: #ff6a95;
        color: #fff;
    }
</style>

<ul class="rating">
    {#each RatingData as item (item.value)}
        <li>
            <input
                type="radio"
                id={item.id}
                name="rating"
                value={item.value}
                on:change={onChange}
                checked={selected === item.value} />
            <label for={item.id}>{item.value}</label>
        </li>
    {/each}
</ul>
