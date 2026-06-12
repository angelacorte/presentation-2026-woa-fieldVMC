+++

title = "FieldVMC: an Asynchronous Model and Platform for Self-Organising Morphogenesis of Artificial Structures"
description = "Presentation @WOA 2026"
outputs = ["Reveal"]

+++

# FieldVMC: an Asynchronous Model and Platform for Self-Organising Morphogenesis of Artificial Structures

[**Angela Cortecchia**](mailto:angela.cortecchia@unibo.it) <!--<i class="fa-solid fa-computer"></i>-->,
[Danilo Pianini](mailto:danilo.pianini@unibo.it) <!--<i class="fa-solid fa-computer"></i>-->,
[Giovanni Ciatto](mailto:giovanni.ciatto@unibo.it) <!--<i class="fa-solid fa-computer"></i>-->,
and
[Roberto Casadei](mailto:roby.casadei@unibo.it) <!--<i class="fa-solid fa-computer"></i>-->



<div style="text-align: center; width: 100%;">
<img src="example-background.svg" style="width: 40%" />

<!-- <i class="fa-solid fa-computer"></i> Department of Computer Science and Engineering, University of Bologna, Cesena (FC), Italy -->
</div>

---

{{< multicol >}}

{{% col %}}

### Plants
![plant image](images/plant-svgrepo-com.svg)

{{% /col %}}

{{% col %}}

### Organizations
![organization order image](images/organization-order-svgrepo-com.svg)

{{% /col %}}

{{% col %}}

### Flocking swarms
![organization order image](images/flock.svg)

{{% /col %}}

{{</ multicol >}}

# What do they have in common?

**runtime-generated hierarchical structure**

---

# Vascular Morphogenesis Controller (**VMC**)<small>[1]</small>

{{< multicol >}}

{{% col class="col-8"%}}

A model for the growth of artificial structures over time.

Works on <b>tree-like structures</b>, in which every node can get information from the environment.

The leaves of the tree start by sending the amount of <b>success</b> they sense to the root.

The root sends back an amount of <b>resources</b> based on the success received from the leaves, regulating the tickness of their connections.

### Limitations

<i class="fa-solid fa-triangle-exclamation"></i><b> Implicitly synchronous</b>.

<i class="fa-solid fa-triangle-exclamation"></i> Requires an <b> underlying tree structure</b> (can't work on graphs).

{{</ col >}}

{{< col >}}
<div class="r-stack">
  <img
    src="images/tree.svg"
    width="180%"
    height="170%"
  />
  <img
    class="fragment current-visible"
    data-fragment-index="1"
    src="images/treeWithSensing.svg"
    width="180%"
    height="170%"
  />
  <img
    class="fragment current-visible"
    data-fragment-index="2"
    src="images/treeWithSuccess.svg"
    width="180%"
    height="170%"
  />
  <img
    class="fragment current-visible"
    data-fragment-index="3"
    src="images/treeWithResources.svg"
    width="180%"
    height="170%"
  />
  <img
    class="fragment current-visible"
    data-fragment-index="4"
    src="images/treeWithResourcesandSuccess.svg"
    width="180%"
    height="170%"
  />
  <img
      class="fragment current-visible"
      data-fragment-index="5"
      src="images/firstStep.svg"
      width="180%"
      height="170%"
    />
  <img
      class="fragment current-visible"
      data-fragment-index="6"
      src="images/secondStep.svg"
      width="180%"
      height="170%"
    />
  <img
      class="fragment current-visible"
      data-fragment-index="7"
      src="images/thirdStep.svg"
      width="180%"
      height="170%"
    />
  <img
      class="fragment current-visible"
      data-fragment-index="8"
      src="images/fourthStep.svg"
      width="180%"
      height="170%"
    />
  <img
      class="fragment current-visible"
      data-fragment-index="9"
      src="images/fifthStep.svg"
      width="180%"
      height="170%"
    />
  <img
      class="fragment current-visible"
      data-fragment-index="10"
      src="images/sixthStep.svg"
      width="180%"
      height="170%"
    />
  <img
    class="fragment current-visible"
    data-fragment-index="11"
    src="images/graph.svg"
    width="180%"
    height="170%"
  />
</div>
{{< /col >}}
{{< /multicol >}}

<div>
<small style="text-align: left">
<p>[1] Zahadat, P., Hofstadler, D.N., Schmickl, T. "Morphogenesis as a Collective Decision of Agents Competing for Limited Resource: A Plants Approach." 2018.</p>
</small>
</div>

---

# A Possible Solution

Porting VMC into a framework that by-design:
1. supports **graph structures** and
2. features **asynchronous** computations.

If the implementation is feasible,
it will automatically overcome the limitations of the original model.

---

# Meet Aggregate Computing<small>[2]</small>

<img src="./images/acDevices.svg" width=70%>

A macro-programming approach that defines the **collective behavior** of heterogeneous devices in a **self-organizing system**.

Based on the **Field Calculus**<small>[3]</small>, operates by manipulating distributed data structures called *fields*.

<div>
<small style="text-align: left">
[2] Beal, J., Pianini, D., Viroli, M. "Aggregate Programming for the Internet of Things." 2015.</br>
[3] Audrito, G., Viroli, M., Damiani, F., Pianini, D., Beal, J. "A Higher-Order Calculus of Computational Fields." 2019.
</small>
</div>

---

# `FieldVMC`: **Aggregate Computing**-based VMC

## Model

{{< multicol >}}

{{% col class="col-8"%}}
- Nodes can <b>compute</b>.
- Neighboring nodes can <b>communicate</b>.
- Nodes have <b>sensors</b>:</br><em>success, resource, distance, and optionally position.</em>
- Nodes have optional <b>actuators</b>:</br><em>spawning and destroying.</em>

{{%/ col %}}

{{< col >}}
<div class="r-stack">
  <img
    class="fragment current-visible"
    data-fragment-index="0"
    src="images/agent.svg"
    width="100%"
    height="100%"
  />
  <img
    class="fragment current-visible"
    data-fragment-index="1"
    src="images/connection.svg"
    width="180%"
    height="170%"
  />
  <img
    class="fragment current-visible"
    data-fragment-index="2"
    src="images/sensors.svg"
    width="180%"
    height="170%"
  />
  <img
    class="fragment current-visible"
    data-fragment-index="3"
    src="images/actuators.svg"
    width="180%"
    height="170%"
  />
</div>
{{< /col >}}
{{< /multicol >}}

---

# `FieldVMC`: **Aggregate Computing**-based VMC

## Implementation

{{< multicol >}}

{{% col class="text-start col-md-7" %}}

(multiple) **Trees** are built on top of **arbitrary networks** using
the _self-organizing coordination regions_ (SCR)<small>[4]</small> pattern.

<p><b>SCR</b> performs <b>continuously</b>:</p>
<ol>
  <li>Sparse <b>leader election</b>;</li>
  <li><b>Control region expansion</b> from leaders;</li>
  <li><b>Upstream</b> information <b>flows</b> construction;</li>
  <li><b>Decision-making</b> and <b>downstream propagation</b>.</li>
</ol>

{{%/ col %}}

{{% col %}}
<div class="r-stack">
  <img
    class=" current-visible"
    src="images/network-1.svg"
    width="100%"
    height="100%"
  />
  <img
    class="fragment current-visible"
    data-fragment-index="1"
    src="images/network-candidates.svg"
    width="180%"
    height="170%"
  />
  <img
    class="fragment current-visible"
    data-fragment-index="2"
    src="images/network-leaders.svg"
    width="180%"
    height="170%"
  />
  <img
    class="fragment current-visible"
    data-fragment-index="3"
    src="images/network-regions.svg"
    width="180%"
    height="170%"
  />
    <img
    class="fragment current-visible"
    data-fragment-index="4"
    src="images/network-upstream.svg"
    width="180%"
    height="170%"
  />
    <img
    class="fragment current-visible"
    data-fragment-index="5"
    src="images/network-downstream2.svg"
    width="180%"
    height="170%"
  />
</div>
{{% /col %}}

{{< /multicol >}}


<div>
<small style="text-align: left">
[4] Casadei, R., Pianini, D., Viroli, M., Natali, A. "Self-organising Coordination Regions: A Pattern for Edge Computing." 2019.
</small>
</div>

---

# `FieldVMC`: **Aggregate Computing**-based VMC

<h2>How it works</h2>
<ol>
  <li><strong>Leader</strong>(s) are chosen <strong>dynamically</strong> based on resource availability;</li>
  <li>A <strong>gradient field</strong> defines zones around each leader, organized by distance to their nearest leader;</li>
  <li><strong>Nodes send data to their leader</strong>, forming a hierarchical tree;</li>
  <li>Leaders <strong>distribute resources</strong> based on node performance;</li>
  <li>Nodes <strong>act based on resources and success</strong>, spawning new nodes or self-destructing.</li>
</ol>

<h3> Supported features</h3>

<ul>
  <li><strong>Multiple leaders</strong>: allowing easier management of large network by splitting them in sub-systems;</li>
  <li><strong>Growth and shrink</strong>: different implementations of <em>spawning/destroying</em> strategies can lead to different structures.</li>
  <li><strong>Merge and split</strong>: ihnerits <em>self-organizing</em> capabilities from AC, thus supports network segmentation or merging.</li>
</ul>

---

# Application example: **Germination**

{{< multicol >}}
{{< col >}}
<div class="r-stack">
<img 
  class=""
  src="images/oneRootWithIndex.gif" 
  alt="One root sequence">
  <img
    class="fragment current-visible"
    data-fragment-index="1"
    src="images/oneroot20.png"
    width="180%"
    height="170%"
  />
</div>
{{< /col >}}

{{% col %}}
## Self-Construction
Creates a stable structure starting from a single node.

{{% /col %}}

{{< /multicol >}}

---

# Application example: **cutting**

{{< multicol >}}
{{< col >}}
<div class="r-stack">
<img src="images/cuttingWithIndex.gif" alt="cutting sequence">
  <img
    class="fragment current-visible"
    data-fragment-index="1"
    src="images/cutting27.png"
    width="180%"
    height="170%"
  />
</div>
{{< /col >}}

{{% col %}}
## Self-Repairing

Stabilization in two different structures starting from a damaged one.

{{%/ col %}}

{{</ multicol >}}

---

# Application example: **Grafting**

{{< multicol >}}
{{< col >}}
<div class="r-stack">
<img src="images/graftWithIndex.gif" alt="graft sequence">
  <img
    class="fragment current-visible"
    data-fragment-index="1"
    src="images/graft23.png"
    width="180%"
    height="170%"
  />
</div>
{{< /col >}}

{{% col %}}
## Self-Integration

Merging of two different structures into a single one.

{{%/ col %}}

{{</ multicol >}}

---

# Application example: **Budding**

{{< multicol >}}
{{< col >}}
<div class="r-stack">
<img src="images/graftWithMoreLeadersWithIndex.gif" alt="More leaders sequence">
  <img
    class="fragment current-visible"
    src="images/graftWithMoreLeaders38.png"
    width="190%"
    height="180%"
  />
</div>
{{< /col >}}

{{% col %}}
## Self-Segmentation

Multiple independent subsystems from a single one.

{{%/ col %}}

{{</ multicol >}}

---

# Application example: **Abscission and regrowth**
{{< multicol >}}
{{< col >}}
<div class="r-stack">
<img src="images/graftWithSpawningWithIndex.gif" alt="graft with spawning sequence">
  <img
    class="fragment current-visible"
    src="images/graftWithSpawning60.png"
    width="180%"
    height="170%"
  />
</div>
{{< /col >}}

{{% col %}}
## Self-Optimization

Optimized merging of two different structures.

<!-- Starts from two non-communicating substructures **with** spawn and destroy policies. -->

<!-- Firstly, the two substructures are optimized, -->
<!-- then they get connected due to the spawning of new nodes. -->

<!-- The new global structure reshapes, -->
<!-- optimizing the balance between resources and success. -->
{{%/ col %}}

{{</ multicol >}}

---

# Conclusion & Future works

The approach enables to express morphogenetic algorithm by a **macroscopic perspective** via aggregate computing.

Possible **future directions**:

- Inspect more **dynamics** and **complex organizational scenarios**;
- Investigate the system response to **continuous perturbations**;
- Development of a **software library** of _aggregate morphogenetic blocks_.

---


## Reproducible experiments here!

<img src="images/vmc-qr.svg" alt="Examples repo">
<div style="text-align: center;">
<p><i class="fab fa-github mr-3" style="color: #095aa6;"></i> <a href="https://github.com/angelacorte/fieldVMC">angelacorte/fieldVMC</a></p>
</div>
