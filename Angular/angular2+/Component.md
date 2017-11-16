        @Component({
            selector: 'app-root',
            templateUrl: './app.component.html',
            styleUrls: ['./app.component.css']
        })
        export class AppComponent {
            title: string;
            myHero: string;
            
            constructor(title: string, myHero:string) {
                this.string = string;
                this.myHero = myHero;
            }
        }

Component initialization: Constructor or variable initialization?

### Creating a class for the data

我认为这是一个非常好的实践。

