# Dependency Parser Using Arc-Eager Parsing Algorithm

## Overview

This project implements a dependency parser based on the Arc-Eager parsing algorithm. The parser operates by transitioning through states (configurations) to identify head-word relationships in sentences. It maintains a stack (S) for processed words, a buffer (B) for words yet to be processed, and a set of arcs (A) representing head-word dependency relations. The initial configuration starts with an empty S and A, and B containing all words of a sentence. The goal is to reach a final state where B is empty, indicating that all head-word relationships have been determined.

## Features and Classifier

A linear classifier is employed to predict the transitions between configurations. The classifier utilizes a binary feature vector derived from the current configuration and the transition. Features include token information, POS tags, and dependency relations seen so far. The feature vector's size is calculated based on the vocabulary, POS tags, and dependency relations, specifically tailored for the four possible transitions: LEFT-ARC, RIGHT-ARC, REDUCE, and SHIFT.

## Training

Training involves using a gold-standard dependency graph and an oracle to determine the ideal transitions for a parser given any configuration. The oracle defines rules for choosing between the LEFT-ARC, RIGHT-ARC, REDUCE, and SHIFT transitions based on the presence of certain dependency relations. The classifier's weights are updated by comparing the predicted transition with the gold-standard transition, aiming to minimize prediction errors.

## Implementation Summary

1. **Feature Vector Function**: A function that generates the binary feature vector for a given configuration and transition.
2. **Training with Oracle**: Applying the oracle on the training set to generate training instances, which are then used to train the classifier.
3. **Online Learning**: The classifier is trained in an online learning setting, where weights are updated with each training example.
4. **Inference**: The trained classifier is used to predict transitions on a test set, identifying head-word relationships.
5. **Evaluation**: The Unlabeled Attachment Score (UAS) metric is used to evaluate the performance of the parser, measuring the accuracy of predicted head-word relationships.

## Restrictions

- Only the Numpy library is permitted for the implementation of this project. No other external libraries are allowed.

## Dataset

The training and testing were conducted on the UD-English-GUM dataset, focusing on predicting only the head-word for each word without considering the specific dependency relation for inference.

## Goal

The ultimate goal of this project is to efficiently predict head-word relationships in sentences using a minimalistic approach that relies solely on the Numpy library, demonstrating the capability of linear classifiers in parsing tasks.

