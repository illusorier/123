Components should not fetch or save data

        import { Injectable } from '@angular/core';
        
        @Injectable()
        export class HeroService {
            constructor() {}
        }
        
Notice that the new service imports the Angular `Injectable` symbol and annotates the

Whether it does or it does not, it's a good practice to keep the decorator.

Services could get data from anywhere - a web service, local storage, or a mock data source.

Removing data access from components 