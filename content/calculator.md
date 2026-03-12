---
title: "천호동 재개발 분담금 시뮬레이터"
date: 2026-03-11
draft: false
---

### 🏗️ 내 집의 가치, 데이터로 확인하십시오.
정확한 데이터가 주민의 재산을 지킵니다.

<div id="calculator-box" style="border: 2px solid #ff5a00; padding: 20px; border-radius: 10px; background-color: #fff9f5; color: #333;">
<label style="font-weight: bold;">현재 내 집의 대지 지분 (평): </label>
<input type="number" id="current-land" value="10" style="width: 100px; padding: 5px; border: 1px solid #ccc; border-radius: 4px;"><br><br>

<label style="font-weight: bold;">현재 시세 (3.3㎡당, 만원): </label>
<input type="number" id="market-price" value="3000" style="width: 100px; padding: 5px; border: 1px solid #ccc; border-radius: 4px;"><br><br>

<label style="font-weight: bold;">희망하는 새 아파트 평형: </label>
<select id="target-size" style="padding: 5px; border: 1px solid #ccc; border-radius: 4px;">
<option value="25">25평 (59㎡)</option>
<option value="34">34평 (84㎡)</option>
</select><br><br>

<label style="font-weight: bold;">예상 조합원 분양가 (평당, 만원): </label>
<input type="number" id="avg-sale-price" value="2500" style="width: 100px; padding: 5px; border: 1px solid #ccc; border-radius: 4px;"><br><br>

<button onclick="calculate()" style="background-color: #ff5a00; color: white; border: none; padding: 12px 24px; cursor: pointer; border-radius: 5px; font-weight: bold; font-size: 1.1em;">분담금 계산하기</button>

<div id="result" style="margin-top: 25px; font-size: 1.3em; font-weight: bold; color: #d35400; border-top: 1px dashed #ff5a00; padding-top: 15px;"></div>
</div>

<script>
function calculate() {
    const land = document.getElementById('current-land').value;
    const price = document.getElementById('market-price').value;
    const targetSize = document.getElementById('target-size').value;
    const avgSalePrice = document.getElementById('avg-sale-price').value;

    const assetValue = land * price * 1.05; 
    const newApartmentPrice = targetSize * avgSalePrice; 
    const resultValue = newApartmentPrice - assetValue;

    const resultDiv = document.getElementById('result');
    if(resultValue > 0) {
        resultDiv.innerHTML = `예상 분담금은 약 <span style="color: #e67e22;">[${Math.round(resultValue/10000).toLocaleString()}억 ${Math.round(resultValue%10000)}만원]</span> 입니다.`;
    } else {
        resultDiv.innerHTML = `축하합니다! 약 <span style="color: #27ae60;">[${Math.round(Math.abs(resultValue)/10000).toLocaleString()}억]</span> 원을 환급받으실 것으로 예상됩니다.`;
    }
}
</script>

<p style="font-size: 0.8em; color: #666; margin-top: 10px;">
    ※ 본 계산기는 공시지가 및 인근 시세를 바탕으로 한 <b>단순 추정치</b>입니다. <br>
    ※ 실제 분담금은 향후 조합 설립 및 관리처분계획에 따라 변동될 수 있습니다.
</p>