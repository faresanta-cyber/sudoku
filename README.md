<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SUDOKU FOOTBALL - TÁCTICO</title>
    <style>
        :root { --pasto: #1b5e20; --oro: #ffd700; --linea: #000; }
        body { font-family: 'Arial Black', sans-serif; background: #051405; color: white; margin: 0; display: flex; flex-direction: column; align-items: center; overflow: hidden; }

        /* HEADER */
        .header { background: #000; width: 100%; padding: 10px 0; text-align: center; border-bottom: 3px solid var(--oro); display: flex; justify-content: center; align-items: center; gap: 30px; }
        #progress-header { font-size: 1.8rem; color: var(--oro); }
        #timer { font-size: 2rem; background: #c62828; padding: 5px 20px; border-radius: 8px; border: 2px solid #fff; font-family: monospace; min-width: 100px; }

        /* JUEGO */
        .game-container { display: flex; gap: 20px; padding: 20px; align-items: flex-start; }
        .grid { display: grid; grid-template-columns: repeat(9, 50px); grid-template-rows: repeat(9, 50px); background: var(--linea); border: 8px solid var(--linea); }
        .cell { width: 50px; height: 50px; background: var(--pasto); display: flex; align-items: center; justify-content: center; font-size: 30px; cursor: pointer; border: 1px solid rgba(255,255,255,0.1); }
        
        /* BORDES GRUESOS SUDOKU */
        .cell:nth-child(3n) { border-right: 5px solid var(--linea); }
        .cell:nth-child(9n) { border-right: none; }
        .cell:nth-child(n+19):nth-child(-n+27), .cell:nth-child(n+46):nth-child(-n+54) { border-bottom: 5px solid var(--linea); }

        .selected { background: var(--oro) !important; color: black; }
        .fixed { background: #0e3511; cursor: default; filter: brightness(0.8); }
        .error { background: #ff4444 !important; }

        /* TECLADO */
        .sidebar { background: rgba(0,0,0,0.5); padding: 15px; border-radius: 15px; border: 2px solid var(--oro); }
        .icon-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; }
        .icon-btn { font-size: 30px; width: 65px; height: 65px; border-radius: 8px; background: white; cursor: pointer; border: none; }
        .delete-btn { grid-column: span 3; padding: 15px; background: #ff4444; color: white; border: none; border-radius: 8px; font
