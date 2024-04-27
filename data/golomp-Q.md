INCREASE OPTIMIZER RUNS

Description:
Optimizer variable can optimize costs by increasing the number of runs
to something like 2000 at least in the config. This value is a tuning
parameter for deploy v/s runtime costs. Higher values optimize for lower
runtime cost.

hardhat.config.ts

    const config: any = {
      solidity: {
        version: "0.8.20",
        settings: {
          optimizer: {
            enabled: true,
            runs: 10,
          },
        },
      },

Recommendation:
It is recommended to increase optimizer runs.