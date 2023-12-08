<script>
  let output = "",
    total = 0;

  const operators = ["+", "-", "/", "*"];

  const handleInput = (e) => {
    string = e.target.value;
  };

  const evaluate = (e) => {
    const inp = e.target.dataset.val;

    switch (inp) {
      case "AC":
        output = "";
        total = 0;
        return;
      case "DEL":
        output = output.slice(0, -1);
        if (output !== "") total = eval(output);
        return;
      case "EQL":
        if (output === "") return;
        output = total;
        return;
    }

    if (operators.includes(inp) && output === "") return;

    output += e.target.dataset.val;
    if (output !== "") total = eval(output);
  };
</script>

<div class="calculator">
  <h2>Calcy</h2>

  <section class="display">
    <input type="text" value={output || 0} on:input={handleInput} />
    <span>{total}</span>
  </section>

  <section class="key-grid">
    <button class="key operator" data-val="AC" on:click={evaluate}>A/C</button>
    <button class="key operator" data-val="DEL" on:click={evaluate}>DEL</button>
    <button class="key operator" data-val="/" on:click={evaluate}>/</button>
    <button class="key operator" data-val="*" on:click={evaluate}>*</button>

    <button class="key" data-val="7" on:click={evaluate}>7</button>
    <button class="key" data-val="8" on:click={evaluate}>8</button>
    <button class="key" data-val="9" on:click={evaluate}>9</button>
    <button class="key operator" data-val="-" on:click={evaluate}>-</button>

    <button class="key" data-val="4" on:click={evaluate}>4</button>
    <button class="key" data-val="5" on:click={evaluate}>5</button>
    <button class="key" data-val="6" on:click={evaluate}>6</button>
    <button class="key plus" data-val="+" on:click={evaluate}>+</button>

    <button class="key" data-val="1" on:click={evaluate}>1</button>
    <button class="key" data-val="2" on:click={evaluate}>2</button>
    <button class="key" data-val="3" on:click={evaluate}>3</button>

    <button class="key zero" data-val="0" on:click={evaluate}>0</button>
    <button class="key operator" data-val="PRD" on:click={evaluate}>.</button>
    <button class="key equal" data-val="EQL" on:click={evaluate}>=</button>
  </section>
</div>

<style>
  .calculator {
    --size: 65px;
    --essence-clr: rgb(206, 100, 174);
    --shadow: 0px 5px 10px rgb(190, 182, 182), inset -2px 2px 8px rgb(230, 230, 230);
    --shadow-2: -1px 2px 12px rgb(173, 173, 173), inset -2px 2px 8px rgb(212, 131, 218);

    display: flex;
    flex-direction: column;
    gap: 1em;
    background: #d3d3d3ab;
    padding: 1.85em 1em;
    border-radius: 0.5em;
    box-shadow:
      0 10px 15px -3px rgb(0 0 0 / 0.1),
      0 4px 6px -4px rgb(0 0 0 / 0.1);
    backdrop-filter: blur(10px);

    max-width: calc(var(--size) * 4 + 2em);
  }

  h2 {
    color: var(--essence-clr);
  }

  .display {
    display: flex;
    flex-direction: column;
    gap: 1em;
    max-width: 100%;
  }

  .display > span,
  .display > input {
    display: block;
    box-shadow: var(--shadow);
    text-align: end;
    background-color: #d4d4d470;
  }

  .display > input:nth-child(1) {
    padding: 0.35em 0.45em;
    font-size: 1.75rem;
    border-radius: 0.25em;
    color: #363636;
    overflow-x: auto;
  }

  .display > input:nth-child(1)::-webkit-scrollbar {
    height: 5px;
  }

  .display > input:nth-child(1)::-webkit-scrollbar-track {
    background-color: #9c9c9c;
  }

  .display > input:nth-child(1)::-webkit-scrollbar-thumb {
    background-color: var(--essence-clr);
  }

  .display > span:nth-child(2) {
    padding: 0.35em 0.75em;
    font-size: 1.25rem;
    font-weight: 500;
    border-radius: 0.25em;
    color: rgb(58, 60, 66);
  }

  .key-grid {
    display: grid;
    grid-template-columns: repeat(4, minmax(0, 1fr));
    grid-template-rows: repeat(5, 1fr);
    gap: 0.8em;

    width: calc(4 * var(--size));
    height: calc(5 * var(--size));
  }

  .key {
    --speacial-clr: #d8b5c4;

    display: grid;
    place-items: center;
    background-color: #d7dbec80;
    box-shadow: var(--shadow);
    border-radius: 0.285em;
    font-weight: 600;
    font-size: 1.2rem;
    color: #1b1b1b;
    cursor: pointer;
  }

  .operator {
    color: var(--essence-clr);
  }

  .plus.key {
    grid-row: span 2;
    background-color: var(--essence-clr);
    font-weight: 400;
    font-size: 1.5cqw;
    color: var(--speacial-clr);
    box-shadow: var(--shadow-2);
  }

  .zero.key {
    grid-column: span 2;
  }

  .equal.key {
    background-color: var(--essence-clr);
    color: var(--speacial-clr);
    font-weight: 400;
    font-size: 1.5cqw;
    box-shadow: var(--shadow-2);
  }
</style>
