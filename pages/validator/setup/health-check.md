# Health check

import Callout from 'nextra-theme-docs/callout'
import Markdown from 'markdown-to-jsx'
import Tabs from '../../../components/tabs'
import CodeBlock from '../../../components/code-block'

Check the status of your validator.

* tofnd check: `tofnd` companion process is alive and accessible from `vald`.
* broadcaster check: Your `broadcaster` address is registered and has balance at least 5 AXL.
* operator check: Your valoper address is indeed an Axelar validator in good status. (Possible bad status includes: not in active set, missed too many blocks, jail status, etc.)

This step is not mandatory but it is good practice to help you detect and diagnose problems with your validator.

<Tabs tabs={[
  {
    title: "Mainnet",
    content: <CodeBlock language="bash">
      {"echo my-secret-password | ~/.axelar/bin/axelard health-check --tofnd-host localhost --operator-addr {VALOPER_ADDR} --home ~/.axelar/.vald"}
    </CodeBlock>
  },
  {
    title: "Testnet",
    content: <CodeBlock language="bash">
      {"echo my-secret-password | ~/.axelar_testnet/bin/axelard health-check --tofnd-host localhost --operator-addr {VALOPER_ADDR} --home ~/.axelar_testnet/.vald"}
    </CodeBlock>
  }
]} />

You should see output like:

```yaml
tofnd check: passed
broadcaster check: passed
operator check: passed
```

<Callout emoji="💡">
  Tip: If you do `axelard health-check` within 50 blocks after first becoming a validator then your validator will not yet post a `heartbeat` transaction.

  In this case, your heath check might return `stale_tss_heartbeat`.  Wait 50 blocks for your validator to automatically post a heartbeat transaction and then try `health-check` again.
</Callout>