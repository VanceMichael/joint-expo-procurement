# 合成资料字典

`fixtures/records.json` 是记录数组。`id` 全局唯一，`kind` 是类型，`links` 指向本资料集内的记录。身份按稳定ID判断，不能以名称替代。日期采用ISO 8601；带时区的时间按实际时刻比较。输入可继续新增，样例数量不是产品容量。

## 业务含义

- `quote`：fixtures中的incoming-sealed-quote是供应商合成输入样例，不是系统已公开应答，应用须自行保密存放后续提交。
- `bundleMinor`：整套报价不可按standaloneMinor拆分而继续声称整套折扣，报价指定允许拆分时例外。
- `paymentShare`：仅为成员提议，所有付款额和变更须本人确认；不自动均摊退出份额。
- `deadline`：接收时刻不晚于截止可以参加本轮，需求变更须新轮次，旧回执不跨轮有效。

## 记录与字段

- `member`：示例ID为 `member-a`；业务字段 `budgetMinor`。
- `buying-group`：示例ID为 `group-a`；业务字段 `required`, `deadline`。
- `supplier`：示例ID为 `vendor-a`；业务字段 。
- `item`：示例ID为 `controller-a`；业务字段 `family`, `role`。
- `compatibility`：示例ID为 `compatibility`；业务字段 `allowed`。
- `member-need`：示例ID为 `need-a`；业务字段 `roles`, `paymentShare`。
- `incoming-sealed-quote`：示例ID为 `quote-a`；业务字段 `revision`, `bundleMinor`, `standaloneMinor`, `stock`, `deliveryBy`。
- `incoming-requirement-change`：示例ID为 `need-revised`；业务字段 `required`, `family`, `revision`。
- `incoming-member-withdrawal`：示例ID为 `exit-b`；业务字段 `at`。

`incoming-`类型及申请、提议记录只是可提交的输入事实，不表示已受理、已签认或已执行。对事实的审核、权限控制和业务后果没有在联调程序里实现。

报价JSON只是可重复提交的合成材料。服务端的报价读取权限不可由调用者自行传入角色决定。

`fixtures/actors.json` 的token只供本地演练。应用应从已验证身份取得权限，不能信任请求自行声明的角色。
