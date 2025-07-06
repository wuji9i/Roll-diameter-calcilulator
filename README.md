<!DOCTYPE html>
<html lang="ru">
<head><meta charset="UTF-8"/><meta name="viewport" content="width=device-width,initial-scale=1.0"/><title>Калькулятор диаметра рулона</title><style>body{font-family:Arial,sans-serif;max-width:400px;margin:auto;padding:20px}input,button{width:100%;padding:10px;margin:8px 0;font-size:16px}#result{margin-top:10px;font-weight:bold}</style></head>
<body>
<h2>Калькулятор внешнего диаметра рулона</h2>
<label>Толщина (мм):</label><input type="number" id="thickness" step="any"/>
<label>Ширина (мм):</label><input type="number" id="width" step="any"/>
<label>Внутренний диаметр (мм):</label><input type="number" id="innerDiameter" step="any"/>
<label>Масса рулона (кг):</label><input type="number" id="weight" step="any"/>
<button onclick="calculate()">Рассчитать</button>
<div id="result">Результат появится здесь</div>
<script>
function calculate(){
  const t = parseFloat(document.getElementById("thickness").value);
  const w = parseFloat(document.getElementById("width").value);
  const dInner = parseFloat(document.getElementById("innerDiameter").value);
  const m = parseFloat(document.getElementById("weight").value);
  if(!t||!w||!dInner||!m){
    document.getElementById("result").innerText = "Пожалуйста, заполните все поля.";
    return;
  }
  const density = 7850;
  const volume = m/density;
  const area = volume/(t/1000);
  const area_mm2 = area*1e6;
  const dOuter = Math.sqrt((4*area_mm2/Math.PI)+dInner*dInner);
  document.getElementById("result").innerText = "Внешний диаметр: " + dOuter.toFixed(2) + " мм";
}
</script>
</body>
</html>
