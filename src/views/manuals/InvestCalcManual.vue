<template>
  <div>
    <Doc :markdownContent="content"/>
  </div>
</template>

<script setup lang="ts">
  import Doc from "@/components/Doc.vue";
  const content = 
  `
  # 投资/贷款计算器
  [[TOC]]

  投资/贷款计算器是财务规划和投资分析中的重要工具，它可以帮助个人和企业评估货币随着时间的推移的价值，从而做出更明智的财务决策。
  ## 功能介绍
  该模块总共提供两个功能：
  - 知四求一功能：已知 PV、FV、PMT、I/Y、N 中的四个就可以求出剩下一个
  - 敏感性分析：可以选取除了计算目标变量以外的任意变量作为敏感因此，自行调节其最大值和最小值，即可查看目标变量随着敏感因子变化的变化趋势

  ## 什么是TVM？
  货币时间价值（Time Value of Money，简称TVM）是金融学中的一个基本概念，它指的是由于时间差异导致货币价值的变化。简单来说，今天的一定金额在未来某个时间点的价值可能会高于或低于现在的价值。[投资/贷款计算器](/calc/invest)就是用来帮助我们评估这种变化的工具。

  ## 示例

  假设你有一笔投资，现值为5000美元，年利率为6%，投资期限为5年，使用TVM计算器可以计算出这笔投资的未来价值：
  $$ FV = PV \\times (1 + \\frac{I}{Y})^N $$
  $$ FV = 5000 \\times (1 + 0.06)^5 \\approx 6584.68 $$
  这意味着在5年后，这笔投资将增长到大约6584.68美元。


  ## 注意事项
  - 在输入PMT时，需要注意现金流的方向，通常流入为正，流出为负。
  - PMT的输入除了数值和正负号外，还需注意是期初还是期末支付，期末是默认值。
  - PV与FV分别是期初和期末的一次性现金流量，FV不应包括期末的最后一笔PMT。
  - 当计算不规则现金流时，可能需要分别计算每个现金流的时间价值，然后将它们累加起来。
  `
</script>

<style>

</style>
