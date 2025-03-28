<template>
  <div>
    <Doc :markdownContent="content"/>
  </div>
</template>

<script setup lang="ts">
  import Doc from "@/components/Doc.vue";

  const content = `
  # 知四求一介绍
  [[TOC]]
  ## 五个关键变量
  在金融计算中，有五个关键变量通常被称为知四求一，它们分别是：

  1. **PV (现值)**  
    现值是未来一笔钱在当前时间点的价值。它考虑了资金的时间价值，即未来的资金比现在的资金更不确定，因此需要折现到现在的价值。

  2. **FV (终值)**  
    终值是当前一笔钱在未来某个时间点的价值。它是通过对现值进行复利计算得到的，考虑了投资收益的增长。

  3. **I/Y (利率)**  
    利率是投资或贷款的收益率，通常以百分比表示。它是计算复利的关键因素，直接影响未来价值的大小。

  4. **PMT (付款金额)**  
    付款金额是每期支付的现金流量。在贷款、投资或养老金等场景中，PMT用于计算每期需要支付的金额。

  5. **N (期数)**  
    期数是指在特定时间范围内的支付次数或投资时间段的总数。它与利率和付款金额共同决定最终的现值或终值。

  ## 应用场景

  ### 1. 购房贷款
  假设你想贷款购买一套房子。你知道贷款金额（PV）、贷款利率（I/Y）、贷款期限（N），你可以计算每月需要偿还的金额（PMT）。

  ### 2. 投资未来的教育
  如果你计划为孩子的教育储蓄，你可以确定现有资金（PV）、希望的未来教育费用（FV）、预期的年利率（I/Y），以及存款时间（N），从而计算出每年需要存入的金额（PMT）。

  ### 3. 养老金计划
  在规划养老金时，你可能希望知道在退休时所需的总资金（FV）、现有储蓄（PV）、预期年利率（I/Y）以及还有多少年（N）到达退休年龄，这样可以帮助你计算每月需要存入的养老金（PMT）。
  `;

  
</script>
