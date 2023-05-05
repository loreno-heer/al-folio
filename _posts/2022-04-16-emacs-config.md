---
layout: post
title: Emacs config that works well
date: 2022-04-16 15:09:00
description: Just some sample config code for emacs that works well for maths and LaTeX
tags: emacs
categories: productivity
---


# Setup Emacs for LaTeX and Coding

This is just my commented init file for emacs. I keep it here as a backup in case I reinstall emacs on another machine.

```lisp
(calendar-date-style 'european)
(calendar-week-start-day 1)


(cua-mode t nil (cua-base))
 
 
(cursor-type 'bar)
 
 
(custom-enabled-themes '(smart-mode-line-respectful dracula))

	   
	   
;; start emacs without the intro screen	   
(inhibit-startup-screen t)

;; remove the menu bar for more screen space
(menu-bar-mode nil)

;; for high dpi monitors
(pdf-view-use-scaling t)
(preview-scale-function 1.6)

;; remove scroll and tool bars
(scroll-bar-mode nil)
(tool-bar-mode nil)


(require 'package)
(add-to-list 'package-archives '("melpa" . "https://melpa.org/packages/") t)
;; Comment/uncomment this line to enable MELPA Stable if desired.  See `package-archive-priorities`
;; and `package-pinned-packages`. Most users will not need or want to do this.
;;(add-to-list 'package-archives '("melpa-stable" . "https://stable.melpa.org/packages/") t)
(package-initialize)

;; enable native compilation of packages
(setq package-native-compile t)


;;use pdf tools instead of docview
(pdf-tools-install)


;; smart mode line setup
(setq sml/theme 'respectful)
(sml/setup)

;; hihhlight current line
(global-hl-line-mode +1)

;; company completion in all buffers
(global-company-mode +1)

;; copy paste using ctrl+c,ctrl+v,...
(cua-mode +1)

;; explain shortcuts in mini buffer
(which-key-mode +1)
;;(which-function-mode +1)


(setq company-tooltip-align-annotations t)



;; compose new files by default in unicode
(prefer-coding-system 'utf-8)


;; get automatic reference management
(setq reftex-plug-into-AUCTeX t)
(add-hook 'LaTeX-mode-hook 'turn-on-reftex)


;; remember last emacs session
;; (desktop-save-mode)

;; install lean4 mode
;; (setq load-path (cons "~/src/lean4/lean4-mode" load-path))
;; (require 'lean4-mode)


;; too many jobs seem to confuse the native compilation
(setq native-comp-async-jobs-number 4)

```

