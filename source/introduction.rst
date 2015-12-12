Introduction
============
.. Should introduce the absolute basics

The Omicron Project seeks to provide a platform for managing and scheduling
experimental research for spin physics. If you have an idea for an experiment,
this platform should be able to guide you through drafting your idea,
scheduling lab time to carry it out, and collaborating with your research group
in order to optimize workflow. In addition, this platform will work as a file
store where the results of your experiment can be dumped and viewed. Finally,
the platform will also provide a way for researchers to determine what each
piece of equipment in their lab is doing at any time, enabling use to be
optimized, downtime to be minimized, and issues to be tracked and reported in
a prompt manner.

Audience
--------

This guide is intended for contributors to and stakeholders interested in the
Omicron Project, who wish to understand

   -  The problem that the system is trying to solve
   -  The reasoning behind particular design choices in the platform design
   -  The development process, from contributing to code review
   -  Current and future directions for the project
   -  The basics of developing code for the Omicron Project

At the end of this guide, a reader should be able to understand what is the
purpose of a service in this platform, or a component that this library depends
on. It is assumed that the reader possesses basic knowledge of

   -  `Python`_
   -  `Javascript`_ (specifically, some of the new features introduced with
      `EcmaScript 6`_
   -  `

The Use Case
------------

A user should be able to log in to the system, open a project, and invite other
users to this project as collaborators. The user should then be able to upload
files to the server, and share them with collaborators on the project. File
uploading should be available to automated services as well as individuals.
