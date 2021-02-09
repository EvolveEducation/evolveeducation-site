<template>
  <div class="about">
    <link rel="stylesheet" type="text/css" href="/about.css" />
    <div class="card">
      <h1>Project Description and Objectives</h1>
      <p>
        Lab time is a precious resource; college students compete
        for the opportunity to get into research labs, and grade school 
        students hardly ever get the chance to step foot in one. Our project
        seeks to solve this problem; we will bring the lab to high school 
        and grade school students, using mathematical models constructed from
        peer reviewed articles to emulate bacteria.
      </p>
    </div>
    <div class="card">
      <h1>The Team</h1>
      <div class="row">
        <div class="aboutCard col-md-3">
          <div class="aboutCardPadding">
            <img src="images/joe.png" />
            <p class="description">
              Joe is a Mathematics major at Virginia Tech. For this project he
              handled code development for the simulation and a large chunk of
              the UI. Additionally he handled most bureaucratic matters as the
              project's PI.
            </p>
            <div class="row social-row">
              <div class="col">
                <div class="social-link">
                  <a href="http://conwell.tech/"><i class="far fa-file"></i></a>
                </div>
              </div>
              <div class="col">
                <div class="social-link">
                  <a href="https://www.linkedin.com/in/joe-conwell/"
                    ><i class="fab fa-linkedin"></i
                  ></a>
                </div>
              </div>
              <div class="col">
                <div class="social-link">
                  <a href="https://github.com/jmc529"
                    ><i class="fab fa-github-square"></i
                  ></a>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="aboutCard col-md-3">
          <div class="aboutCardPadding">
            <img src="images/ross.png" />
            <p class="description">
              Ross is a Creative Technologies major at Virginia tech. For this
              project he designed the graphic elements for the UI as well as
              helping implement the graphing asset.
            </p>
            <div class="row social-row">
              <div class="col" />
              <div class="col">
                <div class="social-link">
                  <a href="https://rossw3.myportfolio.com/"
                    ><i class="far fa-file"></i
                  ></a>
                </div>
              </div>
              <div class="col" />
            </div>
          </div>
        </div>
        <div class="aboutCard col-md-3">
          <div class="aboutCardPadding">
            <img src="images/brian.jpg" />
            <p class="description">Brian is a CS major at Virginia Tech. For this project he was 
              responsible for some of the UI elements and the website.</p>
            <div class="row social-row">
              <div class="col">
                <div class="social-link">
                  <a href="https://www.linkedin.com/in/brian-wieder/"
                    ><i class="fab fa-linkedin"></i
                  ></a>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="aboutCard col-md-3">
          <div class="aboutCardPadding">
            <img src="images/nicole.jpg" />
            <p class="description">Nicole is a recent graduate of Virginia Tech who majored in Biology. 
              She currently is pursing a career at CGI. For this project she was 
              responsible for gathering and documenting research on eColi and bacteria
              growth patterns.</p>
            <div class="row social-row">
              <div class="col">
                <div class="social-link">
                  <a href="https://www.linkedin.com/in/nicole-araujo-822a0a136/"
                    ><i class="fab fa-linkedin"></i
                  ></a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="card">
      <h1>Project History</h1>
      <p>
        This project started at <a href="https://www.hackviolet.com/">SheHacksVT</a> 
        (now HackViolet) as an attempt to simulate bacterial growth as an machine learning 
        (ML) model. This was wrote in python and can be found at this public 
        <a href="https://github.com/jfdenton7/evolution-hackathon">repo</a>. Seeing 
        value in it we decided to seek grant funding to further refine and 
        develop our product. We were awraded a student seed grant from ICAT in 
        the spring of 2020, and then started this current project. 
      </p>

      <p>
        We decided to shift to Unity and away from ML for the second
        iteration of our project. We chose Unity as it was something we were all 
        familar with, allowed us to build out to multiple platforms, and render in 3D
        space with little limitations. We decided to shift away from ML as we 
        wanted to create a learning tool and for that we needed to create
        accurate math models of peer reviewed data, not arbitrary data points that
        attempt to fit a curve.
      </p>
    </div>
  </div>
</template>
