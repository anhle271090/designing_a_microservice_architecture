# designing_a_microservice_architecture
<!-- Improved compatibility of back to top link: See: https://github.com/othneildrew/Best-README-Template/pull/73 -->
<a name="readme-top"></a>
<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Don't forget to give the project a star!
*** Thanks again! Now go create something AMAZING! :D
-->



<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]



<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/anhle271090/designing_a_microservice_architecture">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>

  <h3 align="center">Designing a microservice architecture</h3>

  <p align="center">
    This is my real journey of Designing a microservice architecture.
<!--     <br />
    <a href="https://github.com/othneildrew/Best-README-Template"><strong>Explore the docs »</strong></a>
    <br /> -->
    <br />
<!--     <a href="https://github.com/othneildrew/Best-README-Template">View Demo</a>
    ·
    <a href="https://github.com/othneildrew/Best-README-Template/issues">Report Bug</a>
    ·
    <a href="https://github.com/othneildrew/Best-README-Template/issues">Request Feature</a> -->
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

[![Product Name Screen Shot][product-screenshot]](https://example.com)

Starting with frontend developer position and going through many different projects.
I have been working for building microservices system with alot of challenges. So I wrote this project just for reminding me what I have done wrong and right so far.

Here's some of my main points:
* Mistakes that give microservices a bad implementation.
* Correcting mistakes continuously to build a better microservices (I'm sure that It's still not good enough)
* My lessons learned

Of course, this is only my own experiences. Thanks to all the people!

<p align="right">(<a href="#readme-top">back to top</a>)</p>



## Bad microservices

### Context: Third Party Administrator for Insurance Company
My team was responsible for building a system that helps an insurance company branch to manage their policies, claims. Integrate with HO and other company's system.

This section should list any major frameworks/libraries used to bootstrap your project. Leave any add-ons/plugins for the acknowledgements section. Here are a few examples.

* [![Next][Next.js]][Next-url]
* [![React][React.js]][React-url]
* [![Vue][Vue.js]][Vue-url]
* [![Angular][Angular.io]][Angular-url]
* [![Svelte][Svelte.dev]][Svelte-url]
* [![Laravel][Laravel.com]][Laravel-url]
* [![Bootstrap][Bootstrap.com]][Bootstrap-url]
* [![JQuery][JQuery.com]][JQuery-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- GETTING STARTED -->
## Getting Started

Basically, The requirement is about building an Insurance Platform:
* Managing insurance products with three levels and four lines of products
* Allowing to custom product's attribute and premium formular
* Allowing to custom workflow for sales and issuing policies
* Intergrating with multiple insurance providers
* Supporting claim creation
  
## Which approach I used for this platform?
* Domain Driven Design: this is an approach to developing software for complex needs.

### Step 1: Define user stories

This is an example of how to buy an insurance.
<br/>
<i>Note: this is only a simple example. It's not a full work</i>
* User stories
  ```js
  UserStory InsuranceProduct{
	As an "Admin"
	I want to "create" a "InsuranceProduct" with its "SalesProduct", "Product", "ElementaryProduct"
	so that "Manage insurance product"
  }
  
  UserStory PreBuiltQuote{
  	As a "DIB Admin"
  	I want to "create" "PreBuiltQuote" with its "SalesProduct"
  	I want to "calculate" a "PreBuiltQuote" with its "premium"
  	so that "pre-built insurance product for customer so that can be easy for buying"
  }
  
  UserStory QuoteRequest{
  	As a "HC Employee"
  	I want to "submit" a "QuoteRequest" with its "PreBuiltQuote", "CustomerInfo", "LoanId" for a "Quote"
  	I want to read "Quote" with its "Id", "QuoteURL"
  	I want to read "QuoteItem" in "Quote"
  	so that "I can request insurace quote to insurance company"
  }
  
  UserStory Binder{
  	As a "Order system"
  	I want to "create" a "Binder" with its "Quote"
  	I want to "confirm" a "Binder"
  	so that "I can manage Binder for Policy"
  }
  
  UserStory Policy{
  	As a "Quote System"
  	I want to "create" a "Policy" with its "Binder"
  	I want to update a "Policy"
  	I want to read a "Policy" with its "policyId"
  	so that "Manage customer's policy."
  }

  UserStory Order{
  	As a "Quote System"
  	I want to "create" an "Order" with its "OrderItems" for "Customer"
  	I want to "accept" an "Order" with its "Binder" for "Policy"
  	I want to "checkout" "Order" to "Customer"
  	so that "I can issue a policy for quote thought order and payment"
  }
  
  UserStory Payment{
  	As an "Order System"
  	I want to "create" an "Payment" with its "Price", "Code", "PaymentMethod" for "Order"
  	// I want to "pay" a "Payment" to "Order"
  	// I want to "reject" a "Payment"
  	so that "Manage order's payment"
  }
  ```

  
### Step 2: Define Domain Model

<a href="https://github.com/anhle271090/designing_a_microservice_architecture/ddd_strategic_design/InsuranceDomain_simpler_DomainModel.png">
    <img src="ddd_strategic_design/InsuranceDomain_simpler_DomainModel.png" alt="InsuranceDomain_simpler_DomainModel" width="800">
</a>

### Step 3: Define Subdomains
* ProductSubDomain: Aims at promoting the following benefit for a Admin: Manage insurance product
* PreBuiltQuoteSubDomain: Aims at promoting the following benefit for a Admin: pre-built insurance product for customer so that can be easy for buying
* QuoteSubDomain: Aims at promoting the following benefit for a employee: I can request insurace quote to insurance company
* BinderSubDomain: Aims at promoting the following benefit for a Order system: I can manage Binder for Policy
* PolicySubDomain: Aims at promoting the following benefit for a Quote System: Manage customer's policy.
* OrderSubDomain: Aims at promoting the following benefit for a Quote System: I can issue a policy for quote thought order and payment
* PaymentSubDomain: Aims at promoting the following benefit for a Quoter: Manage order's payment

Defining subdomains is challenging because it’s a creative activity (not something you can buy, download or read in a manual).
It requires clear understanding of the business. In my case, I had a chance to meet domain experts and spend enough time with them.

<a href="https://github.com/anhle271090/designing_a_microservice_architecture/ddd_strategic_design/Define_sub_domains.png">
    <img src="ddd_strategic_design/Define_sub_domains.png" alt="Define_sub_domains" width="800">
</a>

### Step 4: Define Bounded Contexts
Bounded context is the hardest thing in my jouney. Till now, I'm still practicing for this step.
</br>
Read more at: [Link](https://martinfowler.com/bliki/BoundedContext.html)
</br>
Here is my example for defining bounded contexts based on the design at step 3:
</br>
* PolicyBoundedContext: PolicySubDomain and BinderSubDomain
* SalesBoundedConext: OrderSubDomain
* FinanceBoundedContext: PaymentSubDomain
* QuoteBoundedContext: PreBuiltQuoteSubDomain and QuoteSubDomain

### Step 5: Bounded Contexts and Context map
After keeping update the design with a lot of new requirements.
</br>
Then I have a better Context Map with some more Bounded Contexts.
</br>
<a href="https://github.com/anhle271090/designing_a_microservice_architecture/ddd_strategic_design/InsuranceDomain_simpler_ContextMap.svg">
    <img src="ddd_strategic_design/InsuranceDomain_simpler_ContextMap.svg" alt="InsuranceDomain_simpler_ContextMap" width="1000">
</a>
</br>
<i>Note: this is only a simple example. It's not a final design</i>

### Installation

_Below is an example of how you can instruct your audience on installing and setting up your app. This template doesn't rely on any external dependencies or services._

1. Get a free API Key at [https://example.com](https://example.com)
2. Clone the repo
   ```sh
   git clone https://github.com/your_username_/Project-Name.git
   ```
3. Install NPM packages
   ```sh
   npm install
   ```
4. Enter your API in `config.js`
   ```js
   const API_KEY = 'ENTER YOUR API';
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- USAGE EXAMPLES -->
## Usage

Use this space to show useful examples of how a project can be used. Additional screenshots, code examples and demos work well in this space. You may also link to more resources.

_For more examples, please refer to the [Documentation](https://example.com)_

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- ROADMAP -->
## Roadmap

- [x] Add Changelog
- [x] Add back to top links
- [ ] Add Additional Templates w/ Examples
- [ ] Add "components" document to easily copy & paste sections of the readme
- [ ] Multi-language Support
    - [ ] Chinese
    - [ ] Spanish

See the [open issues](https://github.com/othneildrew/Best-README-Template/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTACT -->
## Contact

Your Name - [@your_twitter](https://twitter.com/your_username) - email@example.com

Project Link: [https://github.com/your_username/repo_name](https://github.com/your_username/repo_name)

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

Use this space to list resources you find helpful and would like to give credit to. I've included a few of my favorites to kick things off!

* [Choose an Open Source License](https://choosealicense.com)
* [GitHub Emoji Cheat Sheet](https://www.webpagefx.com/tools/emoji-cheat-sheet)
* [Malven's Flexbox Cheatsheet](https://flexbox.malven.co/)
* [Malven's Grid Cheatsheet](https://grid.malven.co/)
* [Img Shields](https://shields.io)
* [GitHub Pages](https://pages.github.com)
* [Font Awesome](https://fontawesome.com)
* [React Icons](https://react-icons.github.io/react-icons/search)

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/othneildrew/Best-README-Template.svg?style=for-the-badge
[contributors-url]: https://github.com/othneildrew/Best-README-Template/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/othneildrew/Best-README-Template.svg?style=for-the-badge
[forks-url]: https://github.com/othneildrew/Best-README-Template/network/members
[stars-shield]: https://img.shields.io/github/stars/othneildrew/Best-README-Template.svg?style=for-the-badge
[stars-url]: https://github.com/othneildrew/Best-README-Template/stargazers
[issues-shield]: https://img.shields.io/github/issues/othneildrew/Best-README-Template.svg?style=for-the-badge
[issues-url]: https://github.com/othneildrew/Best-README-Template/issues
[license-shield]: https://img.shields.io/github/license/othneildrew/Best-README-Template.svg?style=for-the-badge
[license-url]: https://github.com/othneildrew/Best-README-Template/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/othneildrew
[product-screenshot]: images/screenshot.png
[Next.js]: https://img.shields.io/badge/next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white
[Next-url]: https://nextjs.org/
[React.js]: https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB
[React-url]: https://reactjs.org/
[Vue.js]: https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D
[Vue-url]: https://vuejs.org/
[Angular.io]: https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white
[Angular-url]: https://angular.io/
[Svelte.dev]: https://img.shields.io/badge/Svelte-4A4A55?style=for-the-badge&logo=svelte&logoColor=FF3E00
[Svelte-url]: https://svelte.dev/
[Laravel.com]: https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white
[Laravel-url]: https://laravel.com
[Bootstrap.com]: https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white
[Bootstrap-url]: https://getbootstrap.com
[JQuery.com]: https://img.shields.io/badge/jQuery-0769AD?style=for-the-badge&logo=jquery&logoColor=white
[JQuery-url]: https://jquery.com 
