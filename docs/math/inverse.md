# 模意义下的乘法逆元 inverse

计算 $\dfrac{1}{a} \bmod p$。

<div class="grid cards" id="calc" markdown>
- 输入
    <input class="md-input md-input--stretch" id="input-a" type="number" placeholder="原数">
    <br><br>
    <input class="md-input md-input--stretch" id="input-p" type="number" placeholder="模数">
- 输出
    <input class="md-input md-input--stretch" id="output" placeholder="结果" readonly>
</div>

<script>
window.onload = function() {
    register_calc($("#calc"), function(params) {
        a = BigInt(params.a.val()), p = BigInt(params.p.val());
        if(a < 0 || p <= 0) return "参数错误";
        if(p > 1e18) return "超出计算范围";
        if(a > p) return "原数不能大于模数";
        inv = inverse(a, p);
        if(inv == -1) return "无逆元";
        return String(inv);
    }, {a: $("#input-a"), p: $("#input-p")}, $("#output"));
}
</script>
