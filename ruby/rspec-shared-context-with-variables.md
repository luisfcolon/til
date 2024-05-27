# Rspec shared context with variables

Class with a bunch of validations to see if a person can enter our bar and drink.

```ruby
class CanPersonEnterBar
  def initialize(person: person)
    @person = person
  end

  def call
    return false unless person.has_valid_id?
    return false if person.underage?
    return false if person.violates_dresscode?
    return false if person.already_intoxicated?

    true
  end

  private

  attr_reader :person
end
```

Rspec to test `CanPersonEnterBar`. Since `person` is passed in, we are going to stub it. I don't want too much prep code in my contexts - so I created a shared one and will pass it variables to control the tests.

```ruby
describe CanPersonEnterBar do
  describe '#call' do
    subject(:can_enter_bar) { described_class.new(person: person).call }

    let(:person) { instance_double(Person) }

    shared_context 'verify person' do |valid_id: true, underage: false, violates_dresscode: false, already_intoxicated: false|
      before do
        allow(person).to receive(:has_valid_id?).and_return(valid_id)
        allow(person).to receive(:underage?).and_return(underage)
        allow(person).to receive(:violates_dresscode?).and_return(violates_dresscode)
        allow(person).to receive(:already_intoxicated?).and_return(already_intoxicated)
      end
    end

    context 'when person does not have a valid id' do
      include_context 'verify person', valid_id: false

      it { is_expected.to be false }
    end

    context 'when person is underage' do
      include_context 'verify person', underage: true

      it { is_expected.to be false }
    end

    context 'when person violates the dresscode' do
      include_context 'verify person', violates_dresscode: true

      it { is_expected.to be false }
    end

    context 'when person is already intoxicated' do
      include_context 'verify person', already_intoxicated: true

      it { is_expected.to be false }
    end

    context 'when person checks out' do
      include_context 'verify person'

      it { is_expected.to be true }
    end
  end
end
```
