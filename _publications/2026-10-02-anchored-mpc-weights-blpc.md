---
title: "Anchoring Learned MPC Cost Weights on a Deployed Controller: A Scalar Trust Factor Tested at Full Scale"
collection: publications
category: workshops
permalink: /publication/2026-anchored-mpc-weights-blpc
excerpt: 'An anchored parametrization for learned MPC cost-weight adaptation, where a scalar trust factor scales the learned displacement from a deployed controller''s hand-tuned weights — tested on a full-scale autonomous race car.'
date: 2026-10-02
venue: 'IROS 2026 Workshop on Hybrid Architectures for Embodied Autonomy: Bridging Learning, Planning, and Control (BLPC)'
authors: 'H. Jardali, Y. Yu, L. Liu'
gif: '/images/pubs/anchored-mpc.jpg'
video: 'ZJyzij0KSIk'
citation: '<b>Jardali, H.</b>, Yu, Y., &amp; Liu, L. (2026). &quot;Anchoring Learned MPC Cost Weights on a Deployed Controller: A Scalar Trust Factor Tested at Full Scale.&quot; <i>IROS 2026 Workshop on Hybrid Architectures for Embodied Autonomy: Bridging Learning, Planning, and Control (BLPC)</i>.'
---
A network outputs a bounded direction in log-weight space, and a scalar trust factor λ scales the displacement from the hand-tuned cost weights of a deployed MPC: λ = 0 recovers the baseline exactly and λ = 1 applies the full learned policy. This makes the learned policy easy to evaluate offline before deployment. We deployed the method on a full-scale autonomous race car at λ = 0.50 and 0.75, covering 61 km at speeds up to 48 m/s (174 km/h).
