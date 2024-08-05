# CPU vs GPU

When it comes to password cracking, both CPUs and GPUs have their own advantages and are suited to different tools and scenarios. Here's a comparison to help you understand which to use and when.

**CPU Cracking**

**Advantages**:

1. **Flexibility**: CPUs can handle a wider variety of tasks and are better suited for algorithms that involve complex, sequential processing.
2. **Compatibility**: Most password cracking tools can run on a CPU, and many are optimized for CPU usage.
3. **Cost**: CPUs are generally cheaper to implement for smaller-scale tasks.

**Tools Optimized for CPU**:

1. **John the Ripper**:
   * Versatile and supports numerous hashing algorithms.
   * Great for single-threaded and small-scale parallel processing tasks.
   * Suitable for incremental mode and complex rule-based attacks.
   *   Example:

       ```bash
       john --wordlist=wordlist.txt hashes.txt
       ```
2. **Hydra**:
   * Often used for network service brute force attacks.
   * Supports many protocols and services.
   *   Example:

       ```bash
       hydra -l admin -P passwords.txt ssh://target
       ```

**Use Cases**:

* Environments without powerful GPUs.
* Tasks involving complex logic or rules.
* Situations where the cost of GPU hardware isn't justified.

**GPU Cracking**

**Advantages**:

1. **Speed**: GPUs can perform many calculations simultaneously, making them extremely efficient for parallelizable tasks.
2. **Efficiency**: They are much faster than CPUs for tasks like hashing and encryption, which involve repetitive calculations.
3. **Scalability**: You can use multiple GPUs to scale up your cracking efforts.

**Tools Optimized for GPU**:

1. **Hashcat**:
   * One of the fastest password recovery tools.
   * Leverages the power of GPUs for massive parallel processing.
   * Supports various attack modes, including dictionary, brute force, combinator, mask, and hybrid.
   *   Example:

       ```bash
       hashcat -a 0 -m 0 hashes.txt wordlist.txt
       ```
2. **oclHashcat** (an older version of Hashcat):
   * Specialized for GPUs, though now merged into Hashcat.
   * Used for complex hashing algorithms.

**Use Cases**:

* Cracking large lists of hashes.
* Tasks that require high-speed brute force or dictionary attacks.
* Environments equipped with powerful GPU hardware.

**Comparison Summary**

<table data-full-width="true"><thead><tr><th>Feature</th><th>CPU</th><th>GPU</th></tr></thead><tbody><tr><td><strong>Speed</strong></td><td>Slower, but good for complex tasks</td><td>Much faster for repetitive tasks</td></tr><tr><td><strong>Flexibility</strong></td><td>High</td><td>Medium</td></tr><tr><td><strong>Cost</strong></td><td>Lower for small-scale tasks</td><td>Higher due to hardware costs</td></tr><tr><td><strong>Tool Examples</strong></td><td>John the Ripper, Hydra</td><td>Hashcat, oclHashcat</td></tr><tr><td><strong>Best For</strong></td><td>Complex logic, small-scale tasks</td><td>High-speed, large-scale cracking</td></tr></tbody></table>

#### Practical Examples

**John the Ripper (CPU)**:

```bash
john --wordlist=wordlist.txt hashes.txt
```

**Hashcat (GPU)**:

```bash
hashcat -a 0 -m 0 hashes.txt wordlist.txt
```

#### Conclusion

* **Use CPU** for tasks involving complex rules, logic, or where cost is a concern.
* **Use GPU** for high-speed, large-scale password cracking, especially when dealing with large hash lists or requiring massive parallel processing power.

Choosing the right tool and hardware depends on your specific requirements, resources, and the nature of the task at hand.

{% hint style="info" %}
When working with a GPU, ensure the correct drivers are installed. Prefer a bare-metal installation over a VM, especially for NVIDIA on Windows.
{% endhint %}
